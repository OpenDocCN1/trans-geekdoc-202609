

```
190. form.addEventListener('submit', function (event) {
191.     if (form.checkValidity() == false) {
192.         event.preventDefault();
193.         event.stopPropagation();
194.     }
195.     form.classList.add('was-validated');
196. }, false);
197. });
198. }, false);
199. })();
200. </script>
201. </div>
202. </div>
203. <script src="https://code.jquery.com/jquery-3.3.1.slim.min.js"
204.     integrity="sha384-q8i/X+965DzO0rT7abK41JStQIAqVgRvZvpbozo5snXKpYv9FvH8abtTE1Pi6jizo"
205.     crossorigin="anonymous"></script>
206. <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.6/umd/popper.min.js"
207.     integrity="sha384-wHAiFfRl0JNyYfwEtBMjAuKBPNaej1Ygc/CyP2dxK4EtS3Ump9KsGTTf+hJ9oEoQ"
208.     crossorigin="anonymous"></script>
209. <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/js/bootstrap.min.js"
210.     integrity="sha384-B0UglyR+jN8CRmK6ySgOomIV+1pTzqiPrXUSAWsF2FlN5xOPEJOGVYXdr2jXn4Wq"
211.     crossorigin="anonymous"></script>
212. </body>
213. </html>
```

## 练习

- 1. 添加一个“编辑电影”页面，并在详情页添加一个更新电影的按钮。
- 2. 加分项：将“电影类型”字段从逗号分隔的文本字段改为“类型”表。请参阅“从 moviedetails.php 导航到 editmovie.php”一节末尾的附注。

## 处理文件与现有代码的功能新增

> > “我最有效率的日子之一，就是扔掉了一千行代码。”
> 
> >——肯·汤普森

## 19. 处理文件与现有代码的功能新增

在本章中，我们将为*电影列表*应用程序添加上传和显示图片的功能。

假设我们的*电影列表*应用程序已经上线，有用户说：“嘿，我真的很喜欢这个应用，但如果能为每部电影添加一张缩略图那就太棒了。你能做到吗？”

虽然这句话说起来很简单，但添加这一功能确实需要修改不少 PHP 脚本。而且，根据我们的实现方式，可能需要修改所有 PHP 脚本。因此，让用户了解进展并展示不同的用例和截图是有意义的。不过这超出了本书的范围，所以我直接描述我认为这个功能应有的外观、工作方式以及需要修改的内容：

- 1. 在 `movielisting` 数据库表中添加一个字段，用于存储文件信息（详见下文）。
- 2. 创建一个 `images/` 文件夹，用于存放电影图片。
- 3. 修改 `addmovie.php`，使用户能够上传电影图片，并将其添加到数据库中的电影详细信息条目中。同时，在添加电影后，在“添加电影”页面上显示该图片。图片上传应为可选项。
- 4. 修改 `index.php`，在每行电影开头显示电影缩略图。
- 5. 修改 `moviedetails.php`，在“电影详情”页面上显示图片，以便更好地识别电影。
- 6. 修改 `editmovie.php`，使用户能够（或不）上传另一张电影图片，并修改数据库中的电影详细信息条目。
- 7. 修改 `removemovie.php`，在“删除电影”页面上显示图片，以便更好地识别电影。

### 添加用于文件信息的字段

理论上，我们可以上传图片文件并将图片存储在数据库中。然而，数据库是为快速访问而设计的，而图片文件可能很大。因此，这样做可能会降低查询数据库时的检索速度，尤其是在处理大型数据库时。

更好的解决方案是将图片存储在服务器上的 `images/` 文件夹中。然后，我们在 `movielisting` 表中创建一个字符串字段，用于保存上传图片的文件路径位置。

要向现有表中添加新字段，我们需要 ALTER `movielisting` 表。让我们使用 Adminer 来完成。使用浏览器，以 movieguru 身份登录 Adminer，并创建我们的数据库和表（图 19.1）。

如图 19.2 所示，选择 Movie 数据库。

如图 19.3 所示，选择 `movielisting` 表。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_237_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_237_1.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_237_2.png)

## 19. 处理文件与现有代码的功能新增

然后选择“更改表”（图 19.4）。

如图 19.5 所示，点击 `genre` 字段后面的 +，在 `movieListing` 表末尾添加一个新字段。

为 `image_file` 字段设置以下属性，如图 19.6 所示：

- 在 `genre` 下方的“列名”中输入 `image_file`。
- 选择类型为 `varchar`。
- 长度为 `100`。

按下“保存”后，表描述应如图 19.7 所示。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_238_0.png)

图 19.4。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_238_1.png)

图 19.5。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_238_2.png)

图 19.6。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_238_3.png)

图 19.7。

### 创建用于存放上传电影图片文件的文件夹

在你存放 `index.php` 脚本的主 Web 文件夹中（我的位于 /MovieListing），创建一个名为 `images/` 的新文件夹，如图 19.8 所示。

注意，你的 Web 服务器必须拥有向此文件夹写入文件的权限。例如，在 *NIX 系统上，如果你的 Web 服务器（如 Apache）以 `www-data` 用户运行，请确保该文件夹可由同一用户写入。

```
$ cd /var/www/public/html/Movielisting
$ sudo chown www-data images
$ sudo chmod u+w images
```

最好也准备一张通用的图片，用于没有配图的电影列表。我将它命名为 `generic_movie.jpg`。

### 添加上传文件功能

我们想修改 `addmovie.php` 脚本，使用户能够（可选地）上传电影图片，并将其添加到数据库中的电影详细信息条目中。然后，在用户添加新电影后，在页面上显示该图片。下面是我们希望它实现的效果。

当第一次导航到我们的“添加电影”页面时，修改后的表单应该如图 19.9 所示。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_239_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_239_1.png)

## 19. 处理文件与现有代码的功能新增

假设我要添加电影《宁静号》。图 19.10 显示了目前为止的详细信息。

假设我已经下载了一张图片，当我像图 19.11 那样选择**选择文件**时，应该会弹出一个文件浏览器窗口，我可以导航到要上传的图片文件，选择它，然后点击**打开**（图 19.12）。

所选文件的名称现在显示在“选择文件”按钮之后（图 19.13），而不再是“未选择文件”。

一旦我们按下**添加电影**（图 19.16），我们希望看到的添加电影详情页面带有我们上传的图片，如图 19.15 所示。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_240_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_240_1.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_240_2.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_240_3.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_240_4.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_240_5.png)

### 修改表单以允许上传

我们需要在 `addmovie.php` 表单中添加两个主要内容以支持文件上传。首先，我们需要在 `<form>` 元素中添加 `enctype` 属性，并将其设置为 `multipart/form-data`：

```
<form enctype="multipart/form-data" ...>
```

当使用表单上传文件时，文件数据包含在表单数据中。通过将 `<form>` 元素的 `enctype` 属性设置为 `multipart/form-data`，浏览器会知道在发送到 Web 服务器时将文件数据包含在表单数据中。

其次，我们必须向表单添加一个文件输入元素：

```
<input type="file" class="form-control-file"
    id="movie_image_file" name="movie_image_file">
```

在表单中，将文件输入元素放在一个 Bootstrap `form-group row` 内，位于提交按钮之前，如清单 19.1 所示。

# 清单 19.1。

```
1. </div>
2. <div class="form-group row">
3.     <label for="movie_image_file"
4.         class="col-sm-3 col-form-label-lg">电影图片文件</label>
5.     <div class="col-sm-8">
6.         <input type="file" class="form-control-file"
7.             id="movie_image_file" name="movie_image_file">
8.     </div>
9. </div>
10. <button class="btn btn-primary" type="submit"
11.     name="add_movie_submission">添加电影</button>
12. </form>
```

添加上传文件功能会为我们的脚本增加一些代码。因此，最好尽可能将文件处理能力与 `addmovie.php` 脚本解耦，并将此功能放入一组独立的函数中。这种分离是一个良好的设计决策，因为我们还会在“编辑电影”页面中使用此功能。因此，创建一个单独的脚本用于存放图片文件功能。

