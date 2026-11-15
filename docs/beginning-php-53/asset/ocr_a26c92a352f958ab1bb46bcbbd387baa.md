```
try {
    $ce->doWarp( $factor );
} catch ( InputException $e ) {
    echo "<p>Captain's log: Warp factor " . $e->getInvalidWarpFactor() . "?
I must be losing my mind...</p>";
} catch ( FuelException $e ) {
    echo "<p>Captain's log: I'm getting a fuel problem from the
warp engine. It says: '" . $e->getMessage();
    echo "'". We have " . $e->getRemainingFuel() . " dilithium left.
I guess we're not going anywhere.</p>";
} catch ( Exception $e ) {
    echo "<p>Captain's log: Something else happened, I don't know what.
The message is '" . $e->getMessage() . "'.</p>";
}
}

$c = new Captain;
$c->newWarpOrder( 5 );
$c->newWarpOrder( -1 );
$c->newWarpOrder( 12 );
$c->newWarpOrder( 4 );
$c->newWarpOrder( 9 );

?>
</body>
</html>
```

![](bbox=[0.22, 0.575, 0.865, 0.845])

Figure 20-2