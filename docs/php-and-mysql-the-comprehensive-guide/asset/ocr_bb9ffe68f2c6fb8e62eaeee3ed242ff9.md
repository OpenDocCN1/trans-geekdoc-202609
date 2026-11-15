Now each Google API that is to be used must be added. Here, this is only Google Drive:

```
```php
$client->addScope(Google_Service_Drive::DRIVE_METADATA_READONLY);
```
```

The central element is a case distinction that checks whether an access token already exists. It may not yet exist when the user makes the first call. Therefore, in the else case, the user is redirected to oauth2callback.php, where the actual authentication with Google's OAuth identity provider takes place:

```
```php
if (isset($_SESSION['access_token'])) {
    //access to the service
} else {
    $redirect_uri = 'http://localhost/php/oauth2callback.php';
    header('Location: ' . filter_var($redirect_uri, FILTER_SANITIZE_URL));
}
```
```

Last but not least, the if case: In this case, there is already an access token, so our application has permission to access the Google Drive service. For this, simply initialize a new object for the Drive API:

```
```php
$client->setAccessToken($_SESSION['access_token']);
$drive = new Google_Service_Drive($client);
```
```

The file information is then accessed via the files collection using the Nullsafe operator. This is followed by a simple output:

```
```php
$files = $drive?->files?->listFiles()?->getFiles();
foreach ($files as $file) {
    echo $file->getName();
    echo '<br />';
    echo $file->getMimeType();
    echo '<br /><br />';
}
```
```

The following listing shows the complete code.

```
```php
<?php
require_once 'vendor/autoload.php';

session_start();

$client = new Google\\Client();
$client->setAuthConfig('client_secrets.json');
$client->addScope(Google_Service_Drive::DRIVE_METADATA_READONLY);

if (isset($_SESSION['access_token'])) {
```
```