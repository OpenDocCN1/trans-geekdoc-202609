
% Total % Received % Xferd Average Speed Time Time Time

Current

Dload Upload Total Spent Left Speed

100 81.9M 100 81.9M 0 0 34.1M 0 0:00:02 0:00:02 --:--:-- 34.1M

`$ **tar xf google-cloud-sdk-319.0.1-linux-x86_64.tar.gz**`

`$ **./google-cloud-sdk/install.sh**`

Welcome to the Google Cloud SDK!

*--snip--*

Download the current Google Cloud SDK tarball (the version changes frequently!) and extract it. Then, run the `./google-cloud-sdk/install.sh` script.

The installation process asks you questions that pertain to your environ- ment. I snipped them from the output for brevity.

***Initializing the Google Cloud SDK***

You need to authorize the Google Cloud SDK before you’re able to use it to deploy your code. Google makes this process simple compared to AWS.

There’s no need to create credentials and then copy and paste them to the command line. Instead, Google Cloud uses your web browser for authentication and authorization.

The `gcloud init` command is equivalent to the `aws configure` command, in that it will walk you through the configuration of your Google Cloud command line environment:

`$ **./google-cloud-sdk/bin/gcloud init**`

Welcome! This command will take you through the configuration of gcloud.

*--snip--*

Pick cloud project to use:

Moving to the Cloud **341**

1 \[1\] Create a new project

Please enter numeric choice or text value (must exactly match list item): **1**

Enter a Project ID. Note that a Project ID CANNOT be changed later.

Project IDs must be 6-30 characters (lowercase ASCII, digits, or hyphens) in length and start with a lowercase letter. **goxkcd**

*--snip--*

`$ **gcloud projects list**`

PROJECT_ID NAME PROJECT_NUMBER

goxkcd goxkcd 123456789012

The first step in the process will open a page in your web browser to authenticate your Google Cloud SDK with your Google Cloud account. Your command line output may look a little different from the output here if your Google Cloud account has existing projects. For the purposes of this chapter, elect to create a new project 1 and give it a project ID—goxkcd in this example. Your project ID must be unique across Google Cloud. Once you’ve completed this step, you’re ready to interact with Google Cloud from the command line, just as you did with AWS.

***Enable Billing and Cloud Functions***

You need to make sure billing is enabled for your project before it can use Cloud Functions. Visit *https://cloud.google.com/billing/docs/how-to/modify-project/* to learn how to modify the billing details of an existing project. Once enabled, you can then enable your project’s Cloud Functions access. At this point, you can start writing code.

***Defining a Cloud Function***

Cloud Functions uses Go’s module support instead of requiring you to write a stand-alone application as you did for AWS Lambda. This simplifies your code a bit since you don’t need to import any libraries specific to Cloud Functions or define a main function as the entry point of execution.

Listing 14-7 provides the initial code for a Cloud Functions–compatible module.

package gcp

import (

"encoding/json"

"log"

"net/http"

"github.com/awoodbeck/gnp/ch14/feed"

)

var (

rssFeed feed.RSS

feedURL = "https://xkcd.com/rss.xml"

)

**342** Chapter 14

type EventRequest struct {

Previous bool `json:"previous"`

}

type EventResponse struct {

Title string `json:"title"ÙRL string `json:"url"`

Published string `json:"published"`

}

*Listing 14-7: Creating persistent variables and request and response types (* gcp/xkcd .go *)* The types are identical to the code we wrote for AWS Lambda. Unlike AWS Lambda, Cloud Functions won’t unmarshal the request body into an EventRequest for you. Therefore, you’ll have to handle the unmarshaling and marshaling of the request and response payloads on your own.

Whereas AWS Lambda accepted a range of function signatures, Cloud Functions uses the familiar net/http handler function signature: func(http ResponseWriter, \*http.Request), as shown in Listing 14-8.

*--snip--*

func LatestXKCD(w http.ResponseWriter, r \*http.Request) {

var req EventRequest

resp := EventResponse{Title: "xkcd.com", URL: "https://xkcd.com/"}

defer 1func() {

w.Header().Set("Content-Type", "application/json")

out, \_ := json.Marshal(&resp)

\_, \_ = w.Write(out)

}()

if err := 2json.NewDecoder(r.Body).Decode(&req); err != nil {

log.Printf("decoding request: %v", err)

return

}

if err := rssFeed.ParseURL(3r.Context(), feedURL); err != nil {

log.Printf("parsing feed: %v:", err)

return

}

*Listing 14-8: Handling the request and response and optional y updating the RSS feed* *(* gcp/xkcd .go *)*

Like the AWS code, this LatestXKCD function refreshes the RSS feed by using the ParseURL method. But unlike the equivalent AWS code, you need to JSON-unmarshal the request body 2 and marshal the response to JSON 1 before sending it to the client. Even though LatestXKCD doesn’t receive a context in its function parameters, you can use the request’s context 3 to cancel the parser if the socket connection with the client terminates before the parser returns.

Listing 14-9 implements the remainder of the LatestXKCD function.

Moving to the Cloud **343**

 *--snip--*

 switch items := rssFeed.Items(); {

 case req.Previous && len(items) > 1:

 resp.Title = items\[1\].Title

 resp.URL = items\[1\].URL

 resp.Published = items\[1\].Published

 case len(items) > 0:

 resp.Title = items\[0\].Title

 resp.URL = items\[0\].URL

 resp.Published = items\[0\].Published

 }

}

*Listing 14-9: Populating the response with the feed results (* gcp/xkcd .go *)* Like Listing 14-6, this code populates the response fields with the appropriate feed item. The deferred function in Listing 14-8 handles writing the response to the http.ResponseWriter, so there’s nothing further to do here.

***Deploying Your Cloud Function***

You need to address one bit of module accounting before you deploy your code; you need to create a *go.mod* file so Google can find dependencies, because unlike with AWS Lambda, you don’t compile and package the binary yourself. Instead, the code is ultimately compiled on Cloud Functions.

Use the following commands to create the *go.mod* file:

`$ **cd gcp**`

gcp$ **go mod init github.com/awoodbeck/gnp/ch14/gcp**

go: creating new go.mod: module github.com/awoodbeck/gnp/ch14/gcp

gcp$ **go mod tidy**

*--snip--*

gcp$ **cd -**

These commands initialize a new module named *github.com/awoodbeck/*

*gnp/ch14/gcp* and tidy the module requirements in the *go.mod* file.

Your module is ready for deployment. Use the gcloud functions deploy command, which accepts your code’s function name, the source location, and the Go runtime version:

`$ **gcloud functions deploy LatestXKCD --source ./gcp/ --runtime go113 \\**`

**--trigger-http --allow-unauthenticated**

Deploying function (may take a while - up to 2 minutes)...

For Cloud Build Stackdriver Logs, visit:

https://console.cloud.google.com/logs/viewer *--snip--*

Deploying function (may take a while - up to 2 minutes)...done.

availableMemoryMb: 256

buildId: 5d7fee9b-7468-4b04-badc-81015aa62e59

entryPoint: 1LatestXKCD

httpsTrigger:

url: 2https://us-central1-goxkcd.cloudfunctions.net/LatestXKCD

ingressSettings: 3ALLOW_ALL

**344** Chapter 14

labels:

deployment-tool: cli-gcloud

name: projects/goxkcd/locations/us-central1/functions/LatestXKCD

runtime: 4go113

serviceAccountEmail: goxkcd@appspot.gserviceaccount.com

sourceUploadUrl: https://storage.googleapis.com/ *--snip--*

status: ACTIVE

timeout: 60s

updateTime: '2006-01-02T15:04:05.000Z'

versionId: '1'

The addition of the --trigger-http and --allow-unauthenticated flags tells Google you want to trigger a call to your function by an incoming HTTP request and that no authentication is required for the HTTP endpoint.

Once created, the SDK output shows the function name 1, the HTTP endpoint 2 for your function, the permissions for the endpoint 3, and the
