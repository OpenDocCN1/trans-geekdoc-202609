```
const extname = filetypes.test(path.extname(file.originalname).toLowerCase());
const mimetype = filetypes.test(file.mimetype);
if (mimetype && extname) {
  return cb(null, true);
} else {
  cb(new Error("Invalid file type. Only images and PDFs are allowed."));
}
}
app.post('/upload', upload.single('file'), (req, res) => {
  res.json({ message: "File uploaded securely" });
});
```

**AI-driven enhancement:** The AI-generated secure file upload API introduces multiple layers of defense to address serious vulnerabilities often found in unrestricted upload endpoints. Here is how the AI-powered enhancement improves the API:

+   - AI ensures only allowed file types are accepted (e.g., .jpg, .png, .pdf) and blocks potentially dangerous ones like .exe or .php.\n- Large file uploads are restricted by size limits to prevent performance issues or abuse.
- Custom validation checks are applied to reject unsafe or malformed files before server processing.
- User-friendly error messages are displayed when invalid files are uploaded.
- Uploaded files are stored securely, avoiding exposure of internal server paths.

# Impact of AI on API security and hardening