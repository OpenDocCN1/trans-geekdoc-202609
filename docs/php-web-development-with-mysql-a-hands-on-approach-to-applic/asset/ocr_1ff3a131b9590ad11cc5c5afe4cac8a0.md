```
28. placeholder="Enter a cookie you like to eat"
29. required>
30. </div>
31. <button type="submit" class="btn btn-primary"
32. name="cookie_submission">Submit
33. </button>
34. </form>
35. <?php
36. } // User entered favorite cookie, save session variable and redirect to this page
37. elseif (isset($_POST['cookie_submission']) && isset($_POST['entered_cookie'])) {
38. $_SESSION['favorite_cookie'] = $_POST['entered_cookie'];
39.
40. header("Location: {$_SERVER['PHP_SELF']}");
41. exit;
42. }
43. // Output message displaying saved Session variables
44. // then end the current session and delete the Session variables
45. elseif (isset($_SESSION['name']) && isset($_SESSION['favorite_cookie'])) {
46. ?>
47. <h4>
48. Hey <?= $_SESSION['name'] ?>, you like
49. <?= $_SESSION['favorite_cookie'] ?> cookies. Very nice!
50. </h4>
51. <?php
52. session_destroy(); // End the current session
53. $_SESSION =
54. []; // Destroy all session variables in the current session
55. } // Initial navigation to this page, display form asking for name
56. else {
57. ?>
58. <form class="needs-validation" novalidate method="POST"
59. action="<?= $_SERVER['PHP_SELF'] ?>"
60. <div class="form-group">
61. <label for="name"><h4>What is your name?</h4>
62. </label>
63. <input type="text" class="form-control"
64. id="entered_name" name="entered_name"
65. placeholder="Enter your name" required>
66. </div>
67. <button type="submit" class="btn btn-primary"
68. name="name_submission">Submit
69. </button>
70. </form>
71.
72. <?php
73. }
74. ?>
75. </div>
76. </div>
77. <script>
 // JavaScript for disabling form submissions if there are invalid fields
```