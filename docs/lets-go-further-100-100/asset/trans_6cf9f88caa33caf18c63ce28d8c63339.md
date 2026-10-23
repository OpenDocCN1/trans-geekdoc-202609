
扩展和一个 GIN 索引（详情请参阅此帖）。

从客户端来看，使用 `STRPOS()` 方法也更合理，因为他们可以通过在搜索词的前缀或后缀添加 `%` 通配符字符来控制匹配行为（该字符在 URL 查询字符串中需要转义为 `%25`）。例如，要搜索标题以“the”开头的电影，客户端可以发送查询字符串参数 `title=the%25`。

## 排序列表

现在让我们更新我们的 GET `/v1/movies` 端点的逻辑，以便客户端可以控制 JSON 响应中电影的排序方式。

正如我们之前简要解释的那样，我们希望客户端能够通过格式为 `sort={-}{field_name}` 的查询字符串参数来控制排序顺序，其中可选的 `-` 字符用于表示降序排序。例如：

// Sort the movies on the title field in ascending alphabetical order.
/v1/movies?sort=title

// Sort the movies on the year field in descending numerical order.
/v1/movies?sort=-year

在幕后，我们希望将其转换为 SQL 查询中的 `ORDER BY` 子句，这样像 `sort=-year` 这样的查询字符串参数就会产生如下 SQL 查询：

```
SELECT id, created_at, title, year, runtime, genres, version
FROM movies
WHERE (STRPOS(LOWER(title), LOWER($1)) > 0 OR $1 = '')
AND (genres @> $2 OR $2 = '{}')
ORDER BY year DESC --<- Order the result by descending year
```

这里的难点在于，`ORDER BY` 子句的值需要根据客户端的查询字符串值在运行时生成。理想情况下，我们会使用占位符参数将这些动态值插入查询中，但不幸的是，*无法对列名或 SQL 关键字*（包括 `ASC` 和 `DESC`）使用占位符参数。

因此，我们需要使用 `fmt.Sprintf()` 将这些动态值插值到查询中——确保首先将值与严格的白名单进行检查，以防止 SQL 注入攻击。

在使用 PostgreSQL 时，还需要注意返回行的顺序仅由 `ORDER BY` 子句规定的规则保证。从 [官方文档]()：

> 如果未选择排序，则行将以未指定的顺序返回。在这种情况下，实际顺序取决于扫描和连接计划类型以及磁盘上的顺序，但不得依赖它。只有在显式选择排序步骤时，才能保证特定的输出顺序。

这意味着如果我们不包含一个 `ORDER BY` 子句，则 PostgreSQL 可能会以任何顺序返回电影——*并且每次运行查询时顺序可能会或可能不会改变。*

File: internal/data/filters.go

```go
package data

import (
    "strings" // New import

    "greenlight.alexedwards.net/internal/validator"
)

type Filters struct {
    Page         int
    PageSize     int
    Sort         string
    SortSafelist []string
}

// Check that the client-provided Sort field matches one of the entries in
// our safelist
// and if it does, extract the column name from the Sort field by stripping
// the leading
// hyphen character (if one exists).
func (f Filters) sortColumn() string {
    for _, safeValue := range f.SortSafelist {
        if f.Sort == safeValue {
            return strings.TrimPrefix(f.Sort, "-")
        }
    }

    panic("unsafe sort parameter: " + f.Sort)
}

// Return the sort direction ("ASC" or "DESC") depending on the prefix
// character of the
// Sort field.
func (f Filters) sortDirection() string {
    if strings.HasPrefix(f.Sort, "-") {
    return "DESC"
}

    return "ASC"
}

...
```

请注意，`sortColumn()` 函数的构造方式是，如果客户端提供的 `Sort` 值与我们的白名单中的条目不匹配，则会 panic。理论上这种情况不应该发生——`Sort` 值应该已经通过调用 `ValidateFilters()` 函数进行了检查——但这是一个合理的故障保护机制，有助于阻止 SQL 注入攻击发生。

现在让我们更新 `internal/data/movies.go` 文件以调用这些方法，并将返回值插值到 SQL 查询的 `ORDER BY` 子句中。如下所示：

```
File: internal/data/movies.go

package data

import (
    "context"
    "database/sql"
    "errors"
    "fmt" // New import
    "time"

    "greenlight.alexedwards.net/internal/validator"
)
"github.com/lib/pq"
)
...
func (m MovieModel) GetAll(title string, genres []string, filters Filters) ([]*Movie, error) {
    // Add an ORDER BY clause and interpolate the sort column and direction.
    Importantly
    // notice that we also include a secondary sort on the movie ID to ensure
    a
    // consistent ordering.
    query := fmt.Sprintf(`
        SELECT id, created_at, title, year, runtime, genres, version
        FROM movies
        WHERE (to_tsvector('simple', title) @@ plainto_tsquery('simple', $1) OR $1 = '')
        AND (genres @> $2 OR $2 = '{}')
        ORDER BY %s %s, id ASC`, filters.sortColumn(),
filters.sortDirection()

    // Nothing else below needs to change.
    ...
}
```

完成之后，我们就可以准备试用了。

然后重启应用程序，例如，尝试请求按标题降序排列的电影。你应该会得到如下所示的响应：

```
$ curl "localhost:4000/v1/movies?sort=-title"
{
    "movies": [
```
],
    "version": 5
    }
  ]
}
```

## 分页列表

如果你有一个端点返回包含数百或数千条记录的列表，那么出于性能或可用性的原因，你可能希望在该端点上实现某种形式的 *分页*——以便它在单个 HTTP 响应中只返回记录的子集。

为了演示如何做到这一点，在本章中我们将更新 `GET /v1/movies` 端点，使其支持“页面”的概念，并且客户端可以通过我们的 `page` 和 `page_size` 查询字符串参数请求电影列表的特定“页面”。例如：

// Return the 5 records on page 1 (records 1-5 in the dataset)
/v1/movies?page=1&page_size=5

// Return the next 5 records on page 2 (records 6-10 in the dataset)
/v1/movies?page=2&page_size=5

// Return the next 5 records on page 3 (records 11-15 in the dataset)
/v1/movies?page=3&page_size=5

基本上，修改 `page_size` 参数会改变每个“页面”上显示的电影数量，而将 `page` 参数增加一则会显示列表中下一个“页面”的电影。

```
SELECT id, created_at, title, year, runtime, genres, version
FROM movies
WHERE (to_tsvector('simple', title) @@ plainto_tsquery('simple', $1) OR $1 = '')
AND (genres @> $2 OR $2 = '{}')
ORDER BY %s %s, id ASC
LIMIT 5 OFFSET 10
```

让我们首先为 Filters 结构体添加一些辅助方法来计算适当的 LIMIT 和 OFFSET 值。

如果你跟着操作，请继续更新 internal/data/filters.go 文件，如下所示：

```
File: internal/data/filters.go

package data

...

type Filters struct {
    Page        int
    PageSize    int
    Sort        string
    SortSafelist []string
}

...

func (f Filters) limit() int {
    return f.PageSize
}
```

([]*Movie, error) {
    // Update the SQL query to include the LIMIT and OFFSET clauses with placeholder
    parameter values.
    // parameter values.
    query := fmt.Sprintf(`
        SELECT id, created_at, title, year, runtime, genres, version
        FROM movies
        WHERE (to_tsvector('simple', title) @@ plainto_tsquery('simple', $1) OR $1 = '')
        AND (genres @> $2 OR $2 = '{}')
        ORDER BY %s %s, id ASC
        LIMIT $3 OFFSET $4`, filters.sortColumn(), filters.sortDirection())

    ctx, cancel := context.WithTimeout(context.Background(), 3*time.Second)
    defer cancel()

    // As our SQL query now has quite a few placeholder parameters, let's
    collect the
    // values for the placeholders in a slice. Notice here how we call the
    limit() and
    // offset() methods on the Filters struct to get the appropriate values
    for the
    // LIMIT and OFFSET clauses.
    args := []interface{}{title, pq.Array(genres), filters.limit(),
    filters.offset()}

    // And then pass the args slice to QueryContext() as a variadic
    parameter.
    rows, err := m.DB.QueryContext(ctx, query, args...)
    if err != nil {
        return nil, err
    }

    // Nothing else below needs to change.
    ...
}
