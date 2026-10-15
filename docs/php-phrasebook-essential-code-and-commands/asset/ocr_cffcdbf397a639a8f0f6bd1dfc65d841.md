# Converting a String into a Date

The whole magic is put into the PHP function strtot ime(). According to the documentation, it “parse[s] about any English textual date/time description into a UNIX time stamp.” It sounds amazing, and it is amazing. The basis for this is the GNU date syntax; the code at the beginning of this phrase shows some examples for strtot ime().

> NOTE
> At the time of this writing, strtot ime() shows some strange behavior when a relative date is calculated and a change from or to DST is imminent. Also at the time of this writing, PHP’s date/time functions are about be rewritten and amended.

# Determining Sunrise
and Sunset

```
date_sunrise(time(), SUNFUNCS_RET_STRING, 48, 11.5, 90, 1);
date_sunset(time(), SUNFUNCS_RET_STRING, 48, 11.5, 90, 1);
```

Depending on the current location and date, the times for sunrise and sunset can drastically vary. However, formulas exist for determining this value depending on latitude and longitude, and PHP has this functionality integrated into its core starting with PHP 5. All you are required to do is call date_sunrise() and date_sunset(). Both functions expect a number of parameters:

+   - A time stamp (epoche value) of the date for which to determine the sunrise/sunset