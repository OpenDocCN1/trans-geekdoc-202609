+   5. We then implement a `while()` loop and set the midpoint:
   ```
   while ($loop && !$found) {
       $mid = (int) (($upper - $lower) / 2) + $lower;
   ```

+   6. We now get to use the new PHP 7 **spaceship operator**, which gives us, in a single comparison, less than, equal to, or greater than. If less, we set the upper limit to the midpoint. If greater, the lower limit is adjusted to the midpoint. If equal, we're done and home free:
   ```
   switch ($item <=> $binary[$mid]) {
       // $item < $binary[$mid]
       case -1 :
           $upper = $mid;
           break;
       // $item == $binary[$mid]
       case 0 :
           $found = $binary[$mid];
           break;
       // $item > $binary[$mid]
       case 1 :
       default :
           $lower = $mid;
   }

+   7. Now for a bit of loop control. We increment the number of iterations and make sure it does not exceed the size of the list. If so, something is definitely wrong and we need to bail out. Otherwise, we check to see whether the upper and lower limits are the same more than twice in a row, in which case the search item has not been found. Then we store the number of iterations and return whatever was found (or not):
   ```
   $loop = (($iterations++ < $max) && ($done < 1));
   $done += ($upper == $lower) ? 1 : 0;
   }
   $this->iterations = $iterations;
   return $found;