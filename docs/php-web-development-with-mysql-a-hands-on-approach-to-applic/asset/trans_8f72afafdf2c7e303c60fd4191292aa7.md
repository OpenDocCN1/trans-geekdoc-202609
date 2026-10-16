
## 18. 使用 Web 应用程序编辑数据

```
mysqli_query($dbc, $query)
    or trigger_error(
        'Error querying database movieListing: Failed to update movie listing',
        E_USER_ERROR
    );

$nav_link = 'moviedetails.php?id=' . $id_to_update;

header("Location: $nav_link");
exit;
}
```

所以，假设我们想为一部电影增加五分钟，因为 IMDB[5] 可能没有考虑到片尾字幕场景。我们还认为这部电影也适合“Drama”和“Fantasy”类型。因此，我们的编辑可能看起来像图 18.7。

应用程序将用户引导至“Movie Details”页面，在那里他们可以立即看到结果（图 18.8）。

### 意外导航方法

与上一章一样，由于 HTTP 请求来自客户端。理论上，未预期的或恶意的参数可能出现在查询字符串中（甚至是 HTTP POST 的字段参数）。因此，我们可以导航到 editmovie.php 页面的所有其他条件都是非预期的，我们将处理 else 块：

```
else // Unintended page link
{
```

与上一章一样，由于上述所有条件都是我们希望应用程序以特定方式运行的条件，因此最佳实践是将应用程序对不可预测行为的响应放在 else 条件中。在这种情况下，我们只想链接回主要的“Movies I Like” index.php 页面：

[5] IMDB: https://imdb.com

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_228_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_228_1.png)

```
else // Unintended page link - No movie to edit, redirect back to index
{
    header("Location: index.php");
    exit();
}
```

### 完整代码列表

列表 18.14 包含 editmovie.php 页面的完整列表。

### 列表 18.14.

```
1. <html>
2. <head>
3.   <link rel="stylesheet"
4.         href="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/css/bootstrap.min.css"
5.         integrity="sha384-GJzZqFwbIqT1N6wY59FF1BuG..."
6.         crossorigin="anonymous">
7.   <title>Edit a Movie</title>
8. </head>
9. <body>
10. <div class="card">
11.   <div class="card-body">
12.     <h1>Edit a Movie</h1>
13.     <nav class="nav">
14.       <a class="nav-link" href="index.php">Movies I Like</a>
15.     </nav>
16.     <hr/>
17. <?php
18. require_once('dbconnection.php');
19. 
20. $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
21.     or trigger_error(
22.         'Error connecting to MySQL server for ' . DB_NAME,
23.         E_USER_ERROR
24.     );
25. 
26. $genres = [
27.     'Action', 'Adventure', 'Comedy', 'Documentary', 'Drama',
28.     'Fantasy', 'Horror', 'Romance', 'Science Fiction'
29. ];
30. 
31. if (isset($_GET['id_to_edit'])) {
32.     $id_to_edit = $_GET['id_to_edit'];
33. 
34.     $query = "SELECT * FROM movielisting WHERE id = $id_to_edit";
35. 
36.     $result = mysqli_query($dbc, $query)
37.         or trigger_error('Error querying database movielisting', E_USER_ERROR);
```

```
if (mysqli_num_rows($result) == 1) {
$row = mysqli_fetch_assoc($result);
$movie_title = $row['title'];
$movie_rating = $row['rating'];
$movie_director = $row['director'];
$movie_runtime = $row['running_time_in_minutes'];
$movie_genre_text = $row['genre'];
$checked_movie_genres = explode(', ', $movie_genre_text);
}
} elseif (isset($_POST['edit_movie_submission'], $_POST['movie_title'],
$_POST['movie_rating'], $_POST['movie_director'],
$_POST['movie_running_time_in_minutes'])) {
$movie_title = $_POST['movie_title'];
$movie_rating = $_POST['movie_rating'];
$movie_director = $_POST['movie_director'];
$movie_runtime = $_POST['movie_running_time_in_minutes'];
$checked_movie_genres = $_POST['movie_genre_checkbox'];
$id_to_update = $_POST['id_to_update'];
$movie_genre_text = "";
if (isset($checked_movie_genres)) {
$movie_genre_text = implode(", ", $checked_movie_genres);
}
$query = "UPDATE movielisting SET title = '$movie_title', rating = '$movie_rating', "
. "director = '$movie_director', running_time_in_minutes = '$movie_runtime', "
. "genre = '$movie_genre_text' "
. "WHERE id = $id_to_update";
mysqli_query($dbc, $query)
or trigger_error(
'Error querying database movielisting: Failed to update movie listing',
E_USER_ERROR
);
$nav_link = 'moviedetails.php?id=' . $id_to_update;
header("Location: $nav_link");
exit;
} else // Unintended page link - No movie to edit, link back to index
{
header("Location: index.php");
exit;
}
?>
<form class="needs-validation" novalidate method="POST"
action="<?php echo $_SERVER['PHP_SELF']; ?>">
```

```
<div class="form-group row">
    <label for="movie_title"
           class="col-sm-3 col-form-label-lg">Title</label>
    <div class="col-sm-8">
        <input type="text" class="form-control"
               id="movie_title" name="movie_title"
               value="<?= $movie_title ?>"
               placeholder="Title" required>
        <div class="invalid-feedback">
            Please provide a valid movie title.
        </div>
    </div>
</div>
<div class="form-group row">
    <label for="movie_rating"
           class="col-sm-3 col-form-label-lg">Rating</label>
    <div class="col-sm-8">
        <select class="custom-select" id="movie_rating"
                name="movie_rating"
                value="<?= $movie_rating ?>" required>
            <option value="" disabled selected>Rating...
            </option>
            <option value="G" <?= $movie_rating == 'G' ? 'selected' : '' ?>>G
            </option>
            <option value="PG" <?= $movie_rating == 'PG' ? 'selected' : '' ?>>PG
            </option>
            <option value="PG-13" <?= $movie_rating == 'PG-13' ? 'selected' : '' ?>>PG-13
            </option>
            <option value="R" <?= $movie_rating == 'R' ? 'selected' : '' ?>>R
            </option>
        </select>
        <div class="invalid-feedback">
            Please select a movie rating.
        </div>
    </div>
</div>
<div class="form-group row">
    <label for="movie_director"
           class="col-sm-3 col-form-label-lg">Director</label>
    <div class="col-sm-8">
        <input type="text" class="form-control"
               id="movie_director" name="movie_director"
               value="<?= $movie_director ?>"
               placeholder="Director" required>
        <div class="invalid-feedback">
            Please provide a valid movie director.
        </div>
    </div>
</div>
<div class="form-group row">
```

```
140. <label for="movie_running_time_in_minutes"
141. class="col-sm-3 col-form-label-lg">Running Time (min)</label>
142. <div class="col-sm-8">
143. <input type="number" class="form-control"
144. id="movie_running_time_in_minutes"
145. name="movie_running_time_in_minutes"
146. value="<?= $movie_runtime ?>"
147. placeholder="Running time (in minutes)"
148. required>
149. <div class="invalid-feedback">
150. Please provide a valid running time in minutes.
151. </div>
152. </div>
153. </div>
154. <div class="form-group row">
155. <label class="col-sm-3 col-form-label-lg">Genre</label>
156. <div class="col-sm-8">
157. <?php
158. foreach ($genres as $genre) {
159. ?>
160. <div class="form-check form-check-inline col-sm-3">
161. <input class="form-check-input"
162. type="checkbox"
163. id="movie_genre_checkbox_action_<?= $genre ?>"
164. name="movie_genre_checkbox[]"
165. value="<?= $genre ?>"
166. <?= in_array($genre, $checked_movie_genres) ? 'checked' : '' ?>>
167. <label class="form-check-label"
168. for="movie_genre_checkbox_action_<?= $genre ?>"><?= $genre ?></label>
169. </div>
170. <?php
171. }
172. ?>
173. </div>
174. </div>
175. <button class="btn btn-primary" type="submit"
176. name="edit_movie_submission">Update Movie
177. </button>
178. <input type="hidden" name="id_to_update"
179. value="<?= $id_to_edit ?>">
180. </form>
181. <script>
182. // Javascript for disabling form submissions if there are invalid fields
183. (function () {
184. 'use strict';
185. window.addEventListener('load', function () {
186. // Fetch all the forms we want to apply custom Bootstrap validation styles to
187. var forms = document.getElementsByClassName('needs-validation');
188. // Loop over them and prevent submission
189. var validation = Array.prototype.filter.call(forms, function (form) {
```
