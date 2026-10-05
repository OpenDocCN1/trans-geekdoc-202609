# Chapter 8. File Handling

```
defer zipper.Close()
for, name := range files {
    if err := writeFileToZip(zipper, name); err != nil {
        return err
    }
}
return nil
```

This function creates an empty .zip file, then creates a *zip.Writer (zipper) to write to the file, and then iterates over all of the files, writing each one in turn to the .zip file.

The createZip() and writeFileToZip() functions are very short and so it might be tempting to incorporate them into a single function. This would be unwise if it meant that in the loop we would open file after file (i.e., all those in the file slice), and might exceed the operating system's capacity for open files—something we discussed briefly in the previous chapter (352). Of course, by deferring of the os.File.Close() calls we could do them at each iteration; but this would take some care to ensure that the file is closed whether or not an error occurs. The simplest and cleanest solution to always create a separate function for handling each individual file as we have done here.

```
func writeFileToZip(zipper *zip.Writer, filename string) error {
    file, err := os.Open(filename)
    if err != nil {
        return err
    }
    defer file.Close()
    info, err := file.Stat()
    if err != nil {
        return err
    }
    header, err := zip.FileHeader(info)
    if err != nil {
        return err
    }
    header.Name = sanitizedName(filename)
    writer, err := zipper.CreateHeader(header)
    if err != nil {
        return err
    }
    _, err = io.Copy(writer, file)
    return err
}
```