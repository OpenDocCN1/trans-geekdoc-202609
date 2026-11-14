```
// Service worker registration example
if ('serviceWorker' in navigator) {
  navigator.serviceWorker.register('/sw.js').then(function(registration) {
    console.log('Service Worker registration successful with scope: ', registration
    .scope);
  }).catch(function(error) {
    console.log('Service Worker registration failed:', error);
  });
}
}
```

+   2. Web App Manifest: This JSON configuration file details the app's appearance and behavior on the user's device, supporting home screen installation and full-screen experiences.