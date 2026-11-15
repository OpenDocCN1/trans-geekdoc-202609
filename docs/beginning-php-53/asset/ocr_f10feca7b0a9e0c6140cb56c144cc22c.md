```
<?php

$mapSize = 10;

// Position the home and the pigeons
do {
    $homeX = rand ( 0, $mapSize-1 );
    $homeY = rand ( 0, $mapSize-1 );
    $pigeon1X = rand ( 0, $mapSize-1 );
    $pigeon1Y = rand ( 0, $mapSize-1 );
    $pigeon2X = rand ( 0, $mapSize-1 );
    $pigeon2Y = rand ( 0, $mapSize-1 );
} while ( ( abs($homeX - $pigeon1X) < $mapSize/2 ) && ( abs( $homeY - $pigeon1Y )
< $mapSize/2 ) || ( ( abs($homeX - $pigeon2X ) < $mapSize/2 ) && ( abs( $homeY
- $pigeon2Y ) < $mapSize/2 ) ) );

do {

// Move the pigeons closer to home
if ( $pigeon1X < $homeX )
    $pigeon1X++;
elseif ( $pigeon1X > $homeX )
    $pigeon1X--;
if ( $pigeon1Y < $homeY )
    $pigeon1Y++;
elseif ( $pigeon1Y > $homeY )
    $pigeon1Y--;

if ( $pigeon2X < $homeX )
    $pigeon2X++;
elseif ( $pigeon2X > $homeX )
    $pigeon2X--;
if ( $pigeon2Y < $homeY )
    $pigeon2Y++;
elseif ( $pigeon2Y > $homeY )
    $pigeon2Y--;

// Display the current map
echo '<div class="map" style="width: ' . $mapSize . 'em;"><pre>';
```