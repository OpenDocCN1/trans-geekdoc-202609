# # 17. REMOVING DATA USING THE WEB APPLICATION

```
```php
73. </tr>
74. </tbody>
75. </table>
76. <form method="POST" action="<?= $_SERVER['PHP_SELF'] ?>">
77. <div class="form-group row">
78. <div class="col-sm-2">
79. <button class="btn btn-danger" type="submit" name="delete_movie_submission">
80. Delete Movie
81. </button>
82. </div>
83. <div class="col-sm-2">
84. <button class="btn btn-success" type="submit" name="do_not_delete_movie_submission">
85. Don’t Delete
86. </button>
87. </div>
88. </div>
89. <input type="hidden" name="id" value="<?= $id ?>">
90. </form>
91. <?php
92. else:
93. ?>
94. <h3>No Movie Details :-</h3>
95. <?php
96. endif;
97. else: // Unintended page link - No movie to remove, go back to index
98. header("Location: index.php");
99. exit;
100. endif;
101. ?>
102. </div>
103. </div>
104. <script src="https://code.jquery.com/jquery-3.3.1.slim.min.js"
105. integrity="sha384-DzOOrT7b6V8o9c6jUq3o1rFz4gf1a8tT6trf1OaTjHppL5" crossorigin="anonymous"></script>
106. <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.6/umd/popper.min.js"
107. integrity="sha384-wHAIFRlmFYg5s5Q8K5" crossorigin="anonymous"></script>
108. <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/js/bootstrap.min.js"
109. integrity="sha384-BOgVL0Yy2x8K" crossorigin="anonymous"></script>
110. </body>
111. </html>
```
```