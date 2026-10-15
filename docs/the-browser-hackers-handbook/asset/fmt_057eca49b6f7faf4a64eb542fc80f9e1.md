
```
var ranges = [
'192.168.0.0','192.168.1.0',
'192.168.2.0','192.168.10.0',
'192.168.100.0','192.168.123.0',
'10.0.0.0','10.0.1.0',
'10.1.1.0'
];
var discovered_hosts = [];
// XHR timeout
var timeout = 5000;

function doRequest(host) {
var d = new Date;
var xhr = new XMLHttpRequest();
xhr.onreadystatechange = processRequest;
xhr.timeout = timeout;

function processRequest(){
 if(xhr.readyState == 4){
  var time = new Date().getTime() - d.getTime();
  var aborted = false;
  // if we call window.stop() the event triggered is 'abort'
  // http://www.w3.org/TR/XMLHttpRequest/#event-handlers
  xhr.onabort = function(){
    aborted = true;
  }

  xhr.onloadend = function(){
    if(time < timeout){
      // 'abort' fires always before 'onloadend'
      if(time > 10 && aborted === false){ 
        console.log('Discovered host ['+host+
            '] in ['+time+'] ms');
        discovered_hosts.push(host);
      }
    }
    }
 }
}

xhr.open("GET", "http://" + host, true);
xhr.send();
}

var start_time = new Date().getTime();
function checkComplete(){
    var current_time = new Date().getTime();
    if((current_time - start_time) > timeout + 1000){
        // to stop pending XHRs, especially in Chrome
        window.stop(); 
        clearInterval(checkCompleteInterval);
        console.log("Discovered hosts:\n" + 
            discovered_hosts.join("\n"));
    }
}

var checkCompleteInterval = setInterval(function(){
  checkComplete()}, 1000);

for (var i = 0; i < ranges.length; i++) {
 // the following returns like 192.168.0.
 var c = ranges[i].split('.')[0]+'.'+
 ranges[i].split('.')[1]+'.'+
 ranges[i].split('.')[2]+'.';
 // for every entry in the 'ranges' array, request
 // the most common gateway IPs, like:
 // 192.168.0.1, 192.168.0.100, 192.168.0.254
 doRequest(c + '1');
 doRequest(c + '100');
 doRequest(c + '254');
}
```

This code issues an XHR for every IP of a chosen range, for instance 192.168.0.1 to 192.168.0.50. If the XHR completes in less than xhr_timeout, the destination host is deemed to be alive. If it takes longer than five seconds, the host is deemed to be down. Of course, you might want to adjust these timeouts in instances of higher latency networks.

The WebWorker controller code, used to coordinate the WebWorkers, is the following:
