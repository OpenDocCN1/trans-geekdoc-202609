# 12.1. SEPARATING RESPONSIBILITIES

```
userGorm: userGorm{
  db: db,
}
```

At first glance there isn’t anything wrong with this code. We simply declare each of our layers and construct them inside of one another. Where this starts to become brittle if we wanted to add a new layer, or remove an existing layer.

For example, let's say we wanted to add a cache between the userVal and user-Gorm layers. How would we go about doing that?

We would need to completely change the `userVal` type in order for this to work, updating our code to instead be something like this:

```
type userVal struct {
  userCache
}
func (uv *userVal) ByID(id uint) (*User, error) {
  // Do validations first...
  // We now use the cache instead of the DB layer
  return uv.userCache.ByID(id)
}
type userCache struct {
  userGorm
  // plus other caching data
nfunc (uc *userCache) ByID(id uint) (*User, error) {
  // I am intentionally skipping any caching logic here for
  // simplicity.
  return uc.userGorm.ByID(id)
}
```

We had to completely overhaul the `userVal` type to instead have an embedded `userCache` instead of our database layer, and now our code only works if we have a cache layer present. We cannot use it without a cache.