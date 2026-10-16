# Add Image File Uploads to the Editing Page

```
value='< ?= $movie_rating ?>'
required
<option value="" disabled selected>
Rating...
</option>
<option value="G" <?= $movie_rating = 'G' ? 'selected' : '' ?>>G
<option>
<option value="PG" <?= $movie_rating = 'PG' ? 'selected' : '' ?>>PG
</option>
<option value="PG-13" <?= $movie_rating = 'PG-13' ? 'selected' : '' ?>>PG-13
</option>
<option value="R" <?= $movie_rating = 'R' ? 'selected' : '' ?>>R
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
<div class="col-sm-9">
<input type="text" class="form-control" id="movie_director"
name="movie_director" value="<?= $movie_director ?>"
placeholder="Director" required>
<div class="invalid-feedback">
Please provide a valid movie director.
</div>
</div>
</div>
<div class="form-group row">
<label for="movie_running_time_in_minutes"
class="col-sm-3 col-form-label-lg">Running Time (min)</label>
<div class="col-sm-9">
<input type="number" class="form-control"
id="movie_running_time_in_minutes"
name="movie_running_time_in_minutes"
value="<?= $movie_runtime ?>"
placeholder="Running time (in minutes)"
required>
<div class="invalid-feedback">
Please provide a valid running time in minutes.
</div>
</div>
</div>
<div class="form-group row">
<label class="col-sm-3 col-form-label-lg">Genre</label>
<div class="col-sm-9">
<?php
```