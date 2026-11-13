```
```python
if (r_ > 0.9315) :
    return u'No'
if (r_ <= 0.9315) :
    if (f_ is None) :
        return u'No'
    if (f_ > 0.3) :
        if (f_ > 0.75) :
            return u'No'
        if (f_ <= 0.75) :
            if (f_ > 0.5) :
                return u'No'
            if (f_ <= 0.5) :
                return u'Yes'
if (f_ <= 0.3) :
    return u'No'
if (a_mm_ <= 656) :
    return u'No'
if (fy_mpa_ <= 557) :
    if (r_ is None) :
        return u'No'
if (r_ > 0.9805) :
    if (f_ is None) :
        return u'No'
    if (f_ > 0.3025) :
        if (f_ > 0.46) :
            return u'No'
        if (f_ <= 0.46) :
            return u'Yes'
    if (f_ <= 0.3025) :
        return u'No'
if (r_ <= 0.9805) :
    if (fc_mpa_ is None) :
        return u'Yes'
    if (fc_mpa_ > 46) :
        if (a_mm_ is None) :
            return u'No'
        if (a_mm_ > 431) :
            return u'No'
        if (a_mm_ <= 431) :
            return u'Yes'
    if (fc_mpa_ <= 46) :
        if (a_mm_ is None) :
            return u'Yes'
        if (a_mm_ > 1376) :
            if (r_ > 0.142) :
                return u'No'
            if (r_ <= 0.142) :
                return u'Yes'
        if (a_mm_ <= 1376) :
            return u'Yes'
if (fy_mpa_ <= 413) :
    return u'Yes'
```
```