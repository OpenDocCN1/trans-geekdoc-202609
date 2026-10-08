# Listing 18.4 ftp_mirror.php–Script to Download New Versions of a File from an FTP Server

```
<!DOCTYPE html>
<html>
<head>
  <title>Mirror Update</title>
</head>
<body>
  <h1>Mirror Update</h1>

<?php
  // set variables - change these to suit application
  $host = 'apache.cs.utah.edu';
  $user = 'anonymous';
  $password = 'me@example.com';
  $remotefile = '/apache.org/http/httpd-2.4.16.tar.gz';
  $localfile = '/path/to/files/httpd-2.4.16.tar.gz';

  // connect to host
  $conn = ftp_connect($host);

  if (!$conn) {
    echo 'Error: Could not connect to '.$host;
    exit;
  }

  echo 'Connected to '.$host.'<br />';

  // log in to host
  $result = ftp_login($conn, $user, $pass);
  if (!$result) {
    echo 'Error: Could not log in as '.$user;
    ftp_quit($conn);
    exit;
  }

  echo 'Logged in as '.$user.'<br />';

  // Turn on passive mode
  ftp_pasv($conn, true);

  // Check file times to see if an update is required
  echo 'Checking file time...<br />';
  if (file_exists($localfile)) {

```