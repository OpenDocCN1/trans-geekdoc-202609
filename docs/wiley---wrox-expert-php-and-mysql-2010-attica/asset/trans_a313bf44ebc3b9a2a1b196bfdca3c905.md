
```
return NULL;

$row= $result->fetch_array();
return $row[0];
}
```

getContent() 方法获取文档 id 的内容（url 和 url_content 表查询中指定的记录的 id 值）。数组 $search_results 包含来自 Sphinx 搜索的数据，其中包括找到的记录的 id 值（$search_results['matches']）。接下来，一个循环尝试首先为每个 ID（id）尝试从 memcached 获取内容，如果找到则将该 id 从列表中移除，该列表最终会传递给数据库查询以从 url_content 表获取内容。剩余的任何 id 值都使用 implode() 指定在 IN 列表中。查询结果返回，如果有结果，则获取结果集的每一行并将其与从 memcached 检索到的任何结果一起推入 $results 数组。内容以获取行的 $row[5] 形式找到，被推入 $docs 数组。此 $docs 数组传递给 Sphinx PHP API 方法 BuildExcerpts()，该方法为指定术语创建摘要，使用 <em> 在摘要中突出显示该术语。$results 数组包含有关搜索结果的所有内容（除每个文档的摘要外），然后对其进行遍历并为该结果添加摘要。也在循环内，文档被缓存到 memcached 中。

$results 返回给调用程序，即本例中的搜索 worker，搜索 worker 将结果编码为 JSON，索引页面显示结果。

```
protected function getContent($search_results, $search_term)
{
    if (!is_array($search_results["matches"]))
        return NULL;

    $docs= array ();
    $results= array();
    $to_cache = array();
    $cached = array();

    foreach (array_keys($search_results["matches"]) as $match) {
        $doc_key = "docs:" . $match;

        $cached = array();
        $cached = $this->memc->get($doc_key);

        # if there is a match, then we're happy and can use it
        if ($doc) {
            array_push($results, $cached);

            # since we have it already, take it out of list that
            # will be passed to DB
            unset($search_results["matches"][$match]);
        }
    }
    $query= 'SELECT id, url, created, last_updated, title, content ' .
            'FROM url JOIN url_content USING (id) ' .
            'WHERE id IN (' .
implode(",", array_keys($search_results["matches"])) . ')';

$result= $this->dbhCon->query($query);

if ($result) {
    # Changed from earlier - push into array because we need to maintain
    # order, especially if we use Sphinx ordering/grouping
    while($row= $result->fetch_array())
    {
        array_push($results, array('id'            => $row[0],
                                    'url'           => $row[1],
                                    'url_created'   => $row[2],
                                    'url_last_updated' => $row[3],
                                    'url_title'     => $row[4]));

        array_push($docs, $row[5]);
    }
}
# Note: excerpt index must be actual, not distributed index
$options= array('before_match'  => '<em>',
                'after_match'   => '</em>',
                'around'        => 3,
                'single_passage'=> 0,
                'chunk_separator'=> '...',
                'limit'         => 180);

$excerpts= $this->sphinx->BuildExcerpts($docs, $this->sphinxExcerptIndex,
                                        $search_term, $options);

for ($x= 0; $x < count($results); $x++) {
    $results[$x]["url_excerpt"] = $excerpts[$x];
    $doc_key= "docs:". $results[$x]["id"];

    $this->memc->set($doc_key, $results[$x]);
}

return $results;
}
```

searchIndex() 方法用于将搜索查询传递给 Sphinx 并检索该搜索的结果。此方法由搜索 worker 调用。searchIndex() 的结果是 getContent() 用于获取搜索结果文档内容的内容。

```
protected function searchIndex($query)
{
    if ($this->sphinx == NULL)
    {
        $this->sphinx= new SphinxClient();
        $this->sphinx->SetServer($this->sphinxHost, $this->sphinxPort);
        $this->sphinx->SetMatchMode($this->sphinxMatchMode);
    }

    return $this->sphinx->Query($query, $this->sphinxIndex);
}
```

verify() 方法验证 URL 是否格式正确。如果 URL 值不包含 scheme（http://），则将其添加到 URL 开头。

```
protected function verify($url)
{
    if (strstr($url, "://"))
    {
        if (substr($url, 0, 7) != "http://"
            && substr($url, 0, 8) != "https://")
            return NULL;
    }
    else
        $url= "http://$url";

    if (substr_count($url, "/") == 2)
        $url= "$url/";

    return $url;
}
```

runWorker() 方法是每个 PHP worker 工作循环的核心。它设置使用哪些 Gearman 作业服务器和回调函数，然后启动 work() 循环，在该循环中 worker 等待 gearman 作业服务器分配作业。

```
# Derived worker classes should set functionName, define a callback member
# function, and then call this.
public function runWorker()
{
    $worker= new GearmanWorker();

    foreach ($this->gearmanServers as $server)
        $worker->addServer($server[0], $server[1]);

    $worker->addFunction($this->functionName, "NaradaWorkerCallback", $this);

    while ($worker->work());
};
```

NaradaWorkerCallback() 方法是一种通用方法。它作为之前列出的方法 runWorker() 中的回调方法传递。该方法实现不同的地方在于 worker 如何实现 callback() 函数。worker 调用 runWorker()，它将 NaradaWorkerCallback() 设置为回调函数。当回调函数被调用时，它反过来调用 callback() 方法，使用 worker 指定的实现细节。

```
# Callback function for Gearman worker interface.
function NaradaWorkerCallback($job, &$narada)
{
    return $narada->callback($job);
}
?>
```

现在 Narada 类的细节已经解释清楚，你将能够看到每个 worker 的实现方式以及每个 worker 使用的 Narada 方法。

## Gearman Workers

此应用程序利用四个 worker 来处理网页数据检索、缓存、存储和索引的各个部分。以下小节讨论每一个。

### Insert Worker

insert worker 是启动网页抓取过程的 worker。insert worker 由 index.php 索引页面或 fetch worker 调用。URL 的初始插入会导致 insert worker 将 URL 插入数据库，然后调用 fetch worker，后者反过来为网页内容中获得的任何 URL 调用 insert worker——从而为 Narada 实现网络爬取功能。

与所有 worker 一样，insert worker 实现为 Narada 的子类。第一个定义的方法是 __construct() 方法，它设置 worker 的函数名。此函数名是在 gearman 作业服务器上注册的作业名。下一个方法是 callback() 方法。如果你回顾 Narada 类细节时记得，NaradaWorkerCallback() 方法是在 Gearman worker 方法 addFunction() 中指定的回调方法。NaradaWorkerCallback() 然后调用 callback()，这是每个 worker 中实现的内容。如你所见，每个 worker 的大部分功能都将在 callback() 方法中实现。对于 insert worker，这涉及获取 URL 值并通过调用 insert() 方法将其插入数据库。如果插入成功，它将返回 URL 的 ID 值，并使用该 id 调用 fetch worker 以抓取该 URL。

worker 通过实例化 NaradaInsert 对象然后调用 runWorker() 方法启动，该方法运行实际的 worker，正如你在上一节的 Narada 类说明中看到的那样。

```
require('Narada.php');
class NaradaInsert extends Narada
{
    public function __construct()
    {
        parent::__construct();
        $this->functionName= $this->insertFunctionName;
    }

    public function callback($job)
    {
        $url= $job->workload();

        $this->debug("Insert URL: $url");

        $url= $this->verify($url);
        if (!$url)
        {
            $this->debug("Not a valid URL");
            return "Invalid URL";
```
