```
http.Error(w, err.Error(), http.StatusInternalServerError)
return

// Get any previous flashes.
if flashes := session.Flashes(); len(flashes) > 0 {
// Do something with them
for f := range flashes {
    fmt.Println(flashes[f])
}
} else {
// Set a new flash.
session.AddFlash("Flash! Ah-ah, savior of the universe!" + time.Now().String())
}
session.Save(r, w)
}

func main() {
router := mux.NewRouter()
http.Handle("/", router)
router.HandleFunc("/", handler)
http.ListenAndServe(":8999", nil)
}
```