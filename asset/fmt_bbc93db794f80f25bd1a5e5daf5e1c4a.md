
```html
<!DOCTYPE html>
<html lang="en" dir="ltr">

<head>
<meta charset="utf-8">

<!-- Firebase SDK 是始终需要的，必须第一个列出-->
<script src="https://www.gstatic.com/firebasejs/7.1.0/firebaseapp.js"></script>

<!-- 调用身份验证和数据库访问的 Firebase 脚本： -->
<script src="https://www.gstatic.com/firebasejs/7.1.0/firebaseauth.js"></script>
<script src="https://www.gstatic.com/firebasejs/7.1.0/firebasedatabase.js"></script>

<!-- 定义背景和按钮的样式 -->
<style>
body {
  background-color: #0f1724;
  color: #00a8ff;
  font-family: 'Arial';
  font-size: 20px;
}

.btn {
  color: #fff;
  background-color: #1d2025;
  border-color: #11ece5;
  margin-bottom: 40px;
  margin-top: 20px;
  font-size: 20px;
}
</style>
</head>
<body>
```

```html
<!-- 为输入记录部分创建一个标题 -->
<h3 class="Records">Enter Student Records</h3>
<!-- 为 ID 创建标签和输入框 -->
<label for="ID">ID</label>
<input type="text" id="ID" required="required" />
<br>
<!-- 为 Name 创建标签和输入框 -->
<label for="Name">Name</label>
<input type="text" id="Name" required="required" />
<br>
<!-- 为 Course 创建标签和输入框 -->
<label for="Course">Course</label>
<input type="text" id="Course" required="required" />
<br>
<!-- 为 Grade 创建标签和输入框 -->
<label for="Grade">Grade</label>
<input type="text" id="Grade" required="required" />
<br>
<!-- 创建一个按钮调用 Save_Record() 函数以将学生数据保存到 Firebase 数据库 -->
<button type="button" class="btn" onclick="Save_Record()">SAVE IN DATABASE</button>
</body>
</html>
```

## 云计算基础

来自 Firebase 实时数据库的学生数据--

```html
<button type="button" name="Retrive_Record" onclick="Retrieve_Record()">
从数据库中检索 </button>
```

```html
<br><br>
<!-- 创建标签和文本框，用于输出从数据库检索的姓名、课程和 ID -->
```

```html
<label for="Name2"><b>姓名</b></label> <br>
<input type="text" id="Name2">
<br><br>
```

```html
<label for="Course2"><b>课程</b></label> <br>
<input type="text" id="Course2">
<br><br>
```

```html
<label for="Grade"><b>成绩</b></label> <br>
<input type="text" id="Grade2">
<br>
```

```javascript
// Web 应用的 Firebase 配置
// 对于 Firebase JS SDK v7.20.0 及更高版本，
// 此脚本建立了 Web 应用程序与
// experiments-55b7a 项目的实时数据库之间的连接。
```

```javascript
var firebaseConfig = {
apiKey:"AlzaSyB8df_bThov_Ecl2zAuR7cDyq309W32w1s",
authDomain:"fir-experiments-55b7a.firebaseapp.com",
databaseURL:"https://fir-experiments-55b7a.firebaseio.com",
projectId:"fir-experiments-55b7a",
storageBucket:"fir-experiments-55b7a.appspot.com",
messagingSenderId:"155181565375",
appId:"1:155181565375:web:790d04c868115fd4ca748a",
measurementId:"G-JK20E405ET"
};
```

```javascript
// 初始化 Firebase
firebase.initializeApp(firebaseConfig);
firebase.analytics();
function Save_Record() {
```

```javascript
// 获取用户在 HTML 页面上输入的学生 ID、姓名、课程和成绩
```

```javascript
// 并它们存储为变量：

var StdId = document.getElementById('ID');
var StdName = document.getElementById('Name');
var StdCourse = document.getElementById('Course');
var StdGrade = document.getElementById('Grade');
```

// 获取提取出的变量中存储的值：

```javascript
var v1= StdId.value;
var v2= StdName.value;
var v3 = StdCourse.value;
var v4= StdGrade.value;
```

// 创建一个数据库引用变量，指定 Firebase 中的数据库标识符为 Student_Records

```javascript
var dataRef = firebase.database().ref('Student_Records');
```

// 调用子节点，使存储在变量 v1 中的学生 ID

// 成为给定学生记录的键变量，并使用

// set 函数将用户输入的值赋值给数据库

// 中的 Name、Course 和 Grade 字段。

```javascript
dataRef.child(v1).set({
Name: v2,
Course: v3,
Grade: v4
});
```

// 当记录成功保存到数据库时，发送消息。

```javascript
alert("学生记录保存成功");
```

// 清除网页中的字段，以便用户输入

// 新学生的记录。

```javascript
document.getElementById('ID').value = '';
document.getElementById('Name').value = '';
document.getElementById('Course').value = '';
document.getElementById('Grade').value = '';
```

```javascript
function Retrieve_Record(){

// 获取 Web 页面中输入的 ID 值作为变量。

  var enterID= document.getElementById('getID').value;

  // 创建一个数据库引用变量，指定 Firebase 中的
  // 数据库标识符为 Student_Records
  // 调用子函数根据 enterID 变量
  // 识别学生记录。每当请求数据库时，都会返回一个包含
// 数据库存储数据的快照对象（snapshot）。

  firebase.database().ref('Student_Records').child(enterID).on('value',
function(snapshot) {

  // 从快照变量中提取学生姓名、课程和成绩，
//并将它们存储在三个不同的变量中：

  var S_Name = snapshot.val().Name;
  var S_Course = snapshot.val().Course;
  var S_Grade = snapshot.val().Grade;

  // 将检索到的记录的姓名、课程和成绩输出到
// 网页上相应的文本框中：

  document.getElementById('Name2').value=S_Name;
  document.getElementById('Course2').value=S_Course;
  document.getElementById('Grade2').value=S_Grade;

});

alert("学生记录检索成功");
}
</script>
<br>
</body>
</html>
```

当应用程序启动时，会出现图 2.52 所示的网页。

# 64 T. P. Fowdur, L. Babooram, M. N-U-D-Ibn Nazir Rosun and M. Indoonondon

![](img/2b52fde0e707e8c2f05a10309c3f8982_75_0.png)

图 2.52. Student_Records Web 的布局。

注意的是，应用程序目前托管在本地（localhost）上，没有全局可访问的链接。然而，它仍然可以将数据发送到 Firebase 实时数据库，因为列表 2.5 中的脚本包含了建立数据库连接的所有凭据。图 2.53 显示了数据如何从应用程序发送到 Firebase 实时数据库。

![](img/2b52fde0e707e8c2f05a10309c3f8982_75_1.png)

图 2.53. 从 Web App 向数据库保存学生记录。

在发送了图 2.53 所示的数据以及另一个学生的数据后，数据库将包含图 2.54 所示的内容。

## 云计算基础

![](img/2b52fde0e707e8c2f05a10309c3f8982_76_0.png)

图 2.54. 从 Student_Records Web App 输入数据后的数据库内容。

图 2.55 显示了如何通过 Web App 检索学生记录。

![](img/2b52fde0e707e8c2f05a10309c3f8982_76_1.png)

图 2.55. 使用 Student_Records Web App 从数据库检索数据。

下一个目标是使用 Node.js 将应用程序部署到 Firebase 上。这可以通过接下来的步骤来实现。

# 66 T. P. Fowdar, L. Babooram, M. N-D-Ibn Nazir Rosun and M. Indoondonon

1. 将名为 `public` 的文件夹（包含 Student_Records 应用的 index.html 文件）复制到另一个文件夹（例如，test1），如图 2.56 所示。

![](img/2b52fde0e707e8c2f05a10309c3f8982_77_0.png)

图 2.56. 复制 public 文件夹。

2. 在命令提示符上运行以下行安装 Firebase 工具（需要 Node.js）：

```bash
C:\Users\user1>npm install -g firebase-tools
```

3. 退出 Firebase 并重新登录以生成令牌，如图 2.57 所示。

```bash
C:\Users\user1>firebase logout
Invalid refresh token, did not need to deauthorize
> Logged out as p.fowdar.mu
C:\Users\user1>firebase login
Firebase 可选择收集报告信息以改进我们的产品。
Allow firebase to collect reporting information? Yes
To change your collection preference at any time, use "firebase logout".
访问此 URL 登录：
https://accounts.google.com/signin?auth_user=2&id=56J5s5BB6-f6nh84ki.apps.com&redirect_uri%3Dhttp://localhost:5000
Waiting for authentication...
Success! Logged in as p.fowdar@u.mu
C:\Users\user1>
```

4. 输入 `firebase login` 命令后，将打开一个 URL 并选择账户登录 Firebase。必须遵循图 2.58 所示的步骤才能成功登录。

5. 进入项目目录（即 test1）并输入 `init` 初始化项目。之后按 Y 并选择图 2.59 所示列表中的 `hosting`。

```bash
C:\Users\user1>cd test1
C:\Users\user1\test1>firebase init

You're about to initialize a Firebase project in this directory:
C:\Users\user1>
Are you ready to proceed? Yes
Which Firebase features do you want to set up for this folder? Press Space to select features, then Enter to confirm your choices.
(Database) Deploy Firestore Realtime Database Deploy rules and create indexes for Firestore
(Functions) Configure and deploy Cloud Functions
(Hosting) Deploy Firebase hosting sites
(Storage) Deploy Cloud Storage security rules
(Emulators) Set up local emulators for Firebase features
```

图 2.59. Firebase 项目初始化。

6. 之后选择“use existing project”并选择最初关联应用程序的项目，在这种情况下，它是列表中的 `fir-experiments-55b7a` 项目，如图 2.60 所示。

# 68 T. P. Fowdar, L. Babooram, M. U-D-Ibn Nazir Rosun 和 M. Indoondonman

![](img/2b52fde0e707e8c2f05a10309c3f8982_79_0.png)

图 2.60. 将项目目录与 Firebase 项目关联。

7. 然后，我们指定包含项目文件的文件夹（在本例中为 'public'），并在出现图 2.61 所示的下一个提示时按回车。

![](img/2b52fde0e707e8c2f05a10309c3f8982_79_1.png)

图 2.61. Firebase hosting 设置。

8. 针对图 2.62 显示的后续三个点，我们输入 N(no)，因为我们不想将其配置为单页应用，也不想在 Github 上设置部署。此外，我们不希望 html 文件被 firebase 生成的另一个 index.html 文件覆盖。

```
Configure as a single-page app (rewrite all urls to /index.html)? No
Set up atomic builds and deploys with GitHub? No
Wrote public/4.html
File public/index.html already exists. Overwrite? No
Skipping write of public/index.html
Writing configuration to firebase.json
Writing project information to .firebaserc
Writing gitignore file to .gitignore
Firebase initialization complete!
C:\Users\user1>
```

图 2.62. 完成 Firebase 初始化。

9. 最后，通过输入 `firebase deploy` 部署应用，如图 2.63 所示。

部署完成后，firebase 提供了两个 URL，即 'Project Console' 和 'Hosting URL'如图 2.63 底部所示。

## 云计算基础
