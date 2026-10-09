```
<input type="text" name="name"
             value="<?= htmlespecialchars($name) ?>">
Items Per Page:
<select name="limit">
    <?php foreach (ITEMS_PER_PAGE as $item) : ?>
        <option<?= ($item == $limit) ? ' selected' : ' ?>>
            <?= $item ?></option>
    <?php endforeach; ?>
</select>
<input type="submit" />
</form>
<a href="?name=<?= $name ?>&limit=<?= $limit ?>
           &page=<?= $prev ?>">
    &lt; PREV</a>
<a href="?name=<?= $name ?>&limit=<?= $limit ?>
           &page=<?= $next ?>">
    NEXT &gt;</a>
<?= htmlList($limitIterator); ?>
```

The output will look something like this:

![](bbox=[0.25, 0.46, 0.755, 0.67])

Finally, in order to test the recursive iteration of the country database lookup, you will need to include the iterator's library file, as well as the Application\Database\Connection class:

```
define('DB_CONFIG_FILE', '../config/db.config.php');
include (_DIR_ . '/chap_03_developing_functions_iterators_library.
php');
include (_DIR_ . '../Application/Database/Connection.php');
```