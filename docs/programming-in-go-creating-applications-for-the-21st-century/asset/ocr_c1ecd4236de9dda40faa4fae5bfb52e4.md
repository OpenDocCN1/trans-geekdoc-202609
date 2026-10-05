# 8.2. Archive Files

```
ModTime: stat.ModTime(),
	if err := writer.WriteHeader(header); err != nil {
	return err
}
_, err = io.Copy(writer, file)
	return err
```

This function begins by opening the given file for reading and deferring closing the file. It then does a stat on the file to retrieve the file's mode, size, and modification date/time—this data is used to populate the *tar.Header that must be created for each file that is written to the tarball. (In addition we set the header's user and group IDs; these are used on Unix-like systems.) We should always at the very least set the file's filename (the Name field), and we must set its Size field to the size of the file, or the tarball will be invalid.
Once the *tar.Header has been created and populated, we write the header into the tarball. Then, finally, we copy the file's contents into the tarball.

# 8.2.3. Unpacking Zip Archives

Unzipping a .zip file is as straightforward as zipping one, only we must re-create the directory structure if the archive contains filenames that include paths.

```
func unpackZip(filename string) error {
	reader, err := zip.OpenReader(filename)
	if err != nil {
		return err
	}
	defer reader.Close()
	for _, zipFile := range reader.Reader.File {
		name := sanitizedName(zipFile.Name)
		mode := zipFile.Mode()
		if mode.IsDir() {
			if err := os.MkdirAll(name, 0755); err != nil {
				return err
			}
		} else {
			if err := unpackZippedFile(name, zipFile); err != nil {
				return err
			}
		}
	}
}
```