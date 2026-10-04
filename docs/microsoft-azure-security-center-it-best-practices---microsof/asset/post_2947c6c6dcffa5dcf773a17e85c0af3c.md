
## Accessing security alerts from API

Although Azure Security Center has its own dashboard where you can visualize all security alerts, there are some specific scenarios in which you may want to consume the alert via API. This is a common scenario among organizations that want to build their own dashboards and programmatically manipulate all alerts.

In this chapter, you will learn how to leverage the built-in Security Center Representational State Transfer (REST) API and the Microsoft Graph Security API to retrieve alerts using HTTP requests.

## Understanding REST API

Representational State Transfer (REST) APIs are service endpoints that support sets of HTTP operations (methods), which provide create, retrieve, update, or delete access capabilities to the service's resources. A REST API request/response pair can be separated into five components—three for request and two for response—as shown in Figure 10-1.

![](img/4b11e95292819ab1a383a41ef73aedb4_198_0.png)

The first part of the request is the request URI, which is the main address. This address has the following parts:

Structure: (URI-scheme)://{URI-host}/{resource-path}?{query-string}
Example: https://management.azure.com/subscriptions/XXX/providers/Microsoft.Security/alerts/api-version=2019-01-01

The second part is the HTTP request header, which is composed of request HTTP method, such as GET, HEAD, PUT, POST. Also, you may have other optional headers, such as authentication. The third part is optional, and it can contain supplementary information that vary according to the method that was used. For example, a POST method can contain MIME-encoded objects, which means you need to specify the Content-type request header as well.

The first part of the response is the HTTP status code, which can also vary according to how the backend is responding to this request. If everything is working properly and this is a successful request, you should receive an HTTP 200 status code. Also, the second field is optional, and it is there to support the main response, just as in the previous MIME-encoded example.

## Accessing Alerts using Security Center REST API

Security Center has its own set of REST API that are divided in operation groups. The available groups are described below:

- Alerts: These are security alerts on the subscription level.
- Auto Provisioning Settings: These enable you to specify provisioning configuration for the subscription.
- Compliances: This retrieves regulatory compliance information for the subscription.
- Discovered Security Solutions: This retrieves the details about discovered security solutions.
- External Security Solutions: This retrieves the details about partner solutions that are currently integrated with Security Center.
- JIT Network Access Policies: This retrieves policies for protecting resources using Just-in-Time (JIT) VM access.
- Locations: This retrieves details of specific locations.
- Operations: This retrieves all available operations.
- Pricings: This retrieves the pricing tier that is in use by Security Center.
- Security Contacts: This enables you to configure the security contact information for the subscription.
- Tasks: This enables you to visualize Security Center recommendations for the script.
- Workspace Settings: This enables you to configure workspace-related settings.

As you can see, there are lots of operations that can be performed via API; this chapter is only focused on alerts. The Alert call via REST API has many operations that can be performed, including getting alerts for a resource that is associated with a resource group or a subscription. To list all the alerts associated with a resource, you can use the following example:
https://management.azure.com/subscriptions/{subscriptionId}/providers/Microsoft.Security/alerts?api-version=2019-01-01

The response for this HTTP GET should be an HTTP 200 Header, followed by the body in JSON format, as shown in Listing 10-1.

## LISTING 10-1 Response for HTTP GET Request

```json
{
  "value": [
    {
      "id": "/subscriptions/f5bcb5bd4-93d5-4cd0-913b-b4a7ecb1a70/resourceGroups/contososc/microsoft.security/locations/central/alerts/251849388370938726_1d69063a-54f4-4771-9b96-ccfac1cddd35",
      "name": "251849388370938726_1d69063a-54f4-4771-9b96-ccfac1cddd35",
      "type": "Microsoft.Security/Locations/alerts",
      "properties": {
        "systemSource": "Azure",
        "vendorName": "Microsoft",
        "alertDisplayName": "Suspicious PowerShell Activity Detected",
        "alertName": "SCBA_PSINSIGHT",
        "detectedUtc": "2019-03-18T12:34:52.0616732",
        "description": "Analysis of host data detected by a powers script running on %(Compromised Host) that has features in common with known suspicious scripts. This script could either be legitimate activity, or an indication of a compromised host.",
        "remediationSteps": "Review with {User Name} the suspicious script in this alert to see if this is legitimate activity. If not, escalate the alert to the security team.",
        "actionTaken": "Undefined",
        "reportedSeverity": "High",
        "compromisedEntity": "w012READYO",
        "associatedResource": "/subscriptions/{subscriptionId}/resourcegroups/contososc/providers/microsoft.compute/virtualmachines/w012READYO",
        "subscriptionId": "XXXX",
        "instanceId": "XXXX",
        "extendedProperties": {
          "compromisedHost": "w012READYO",
          "userName": "yuri",
          "accountId": "0x871a4aa",
          "suspiciousProcess": "c:\\windows\\system32\\powershell\\v1.0*"
        }
      },
      "exe": "powershell -nop exec -encodedcommand cvahazqbyhmaaaabagawacaoywbag0ubqbhqag4azaagaciajagagahsaiabpbhcacgagaggagadab00ahwaacw6al1wkag8adduwbaagdwhabagqlgbkahzahacwbbpag4adabliabiahghwagwcauagmawwbtac8azbgpagwazqbzc8aw5hbagvbqag41gbqqaacaac0atwlbahqrgbpagwazqwagmaogbnwcahazqtbtaaxzabahyahwoaq8awbcoc0acqb24iapplabqiawacia",
      "suspiciousProcessId": "544",
      "suspiciousScript": "powershell -command { iwr https://download.sysinternals.com/files/Sysmon.zip -OutFile c:\\svhost.exe }",
      "resourceType": "Virtual Machine",
      "state": "Active",
      "reportedUtc": "2019-03-18T12:12:28.5727442",
      "workspaceResourceId": "/subscriptions/XXXX",
      "confidenceScore": 0.494,
      "confidenceReasons": [
        {
          "type": "Process",
          "reason": "Suspicious process powershell.exe triggered this alert on multiple machines in this subscription"
        },
        {
          "type": "Computer",
          "reason": "This alert was triggered multiple times on machine W012READYO in the last 24 hours"
        },
        {
          "type": "User",
          "reason": "User DWM-1 was involved in multiple alerts on machine W012READYO in the last 7 days"
        }
      ],
      "canBeInvestigated": true,
      "isIncident": false,
      "entities": [
        {
          "$id": "centralus_1",
          "dnsDomain": "",
          "ntDomain": "",
          "hostName": "W012READYO",
          "netBiosName": "W012READYO",
          "osFamily": "Windows",
          "osVersion": "Windows",
          "isDomainJoined": false,
          "type": "host"
        },
        {
          "$id": "centralus_2",
          "processId": "0xe18",
          "commandLine": "",
          "host": {
            "$ref": "centralus_1"
          },
          "type": "process"
        },
        {
          "id": "centralus_3",
          "name": "yuri",
          "ntDomain": "W012READYO",
          "host": {
            "ref": "centralus_1"
          },
          "sid": "S-1-5-21-43177023320-132450192-196-3277483117-500",
          "isDomainJoined": false,
          "type": "account",
          "LogonId": "0x871a4"
        },
        {
          "id": "centralus_4",
          "directory": "c:\\windows\\system32\\powershell\\v1.0",
          "name": "powershell.exe",
          "type": "file"
        },
        {
          "id": "centralus_5",
          "processid": "0x5ca4",
          "commandLine": "powershell -nop exec bypass -encodedcommand cvahcazqbyhmaaaabagawacaoywbag0ubqbhqag4azaagaciajagagahsaiabpbhcacgagaggagadab00ahwaacw6al1wkag8adduwbaagdwhabagqlgbkahzahacwbbpag4adabliabiahghwagwcauagmawwbtac8azbgpagwazqbzc8aw5hbagvbqag41gbqqaacaac0atwlbahqrgbpagwazqwagmaogbnwcahazqtbtaaxzabahyahwoaq8awbcoc0acqb24iapplabqiawacia",
          "elevationToken": "Default",
          "creationTime": "2019-03-18T12:34:52.0616273Z",
          "imageFile": {
            "ref": "centralus_4"
          },
          "account": {
            "ref": "centralus_3"
          },
          "parentProcess": {
            "ref": "centralus_2"
          },
          "host": {
            "ref": "centralus_1"
          },
          "type": "process"
        },
        {
          "id": "centralus_6",
          "sessionId": "0x871a4"
        }
      ]
    }
  ]
}
```

Accessing Alerts using Security Center REST API Chapter 10 183
