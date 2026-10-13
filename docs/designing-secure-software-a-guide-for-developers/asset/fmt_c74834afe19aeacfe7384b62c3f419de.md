
## Section 6 – Logger Service API

Each application connects to its logging service via a dedicated channel. **HTTPS secures API invocations between authenticated endpoints; the preconfigured server name authenticates (by its digital certificate) that clients are connected to valid Logger service instances.** The following are the request types.

### 6.1 Hello Request

Any process that will use the Logger service sends this request to initiate the logging:

```json
{"verb": "Hello", "source": "Sample application", "version": "1"}
```

The following response acknowledges the request with an OK or error message and provides a string token for the session:

```json
{"status": "OK", "service": "Logger", "version": "1", "token": "XYZ123"}
```

The token is used in subsequent requests to identify the context of the initiating application corresponding to the `Hello`. **Tokens are generated randomly with sufficient complexity and entropy to preclude guessing: the minimum recommended token size is 120 bits, or about 20 characters in base64 encoding. Shorter tokens are used here for brevity.**

### 6.2 Schema Definition Request

This request defines the data schema for subsequent logging, as described in Section 5:

```json
{"verb": "Schema", "token": "XYZ123", ...}
```

*Details of this request are omitted for brevity.*

The schema defines the field names, types, and other attributes that will appear in the log contents, as illustrated by the sample event log request shown in the following section (which includes the fields `timestamp`, `ipaddr`, `http`, `url`, and `error`).

### 6.3 Event Log Request

This request actually logs one record with the Logger service:

```json
{"verb": "Event", "token": "XYZ123", "log": {
 "timestamp": 1234567890, "ipaddr": "12.34.56.78", 
 "http": "POST", "url": "example", "error": "404"}}
```

The `log` JSON presents content to be recorded to the log that must match the schema.

The response acknowledges the request with an OK or error message:

```json
{"status": "OK"}
```

*Error details are omitted for brevity.* **Logging errors (for example, insufficient storage space) are serious and require immediate attention, since system operation is not auditable in the absence of logging.**

### 6.4 Goodbye Request

This request completes a session of logging:

```json
{"verb": "Goodbye", "token": "XYZ123"}
```

The response acknowledges the request with an OK or error message:

```json
{"status": "OK"}
```

The token thereafter is no longer valid. To resume logging, the client must first make a `Hello` request.

## Section 7 – User Interface Design

The user interface to the Logger is a web interface served by Logger Viewer that is used to examine the logs. **The web app is only accessible by authorized operations staff and authenticated by enterprise single sign-on.** Authenticated users see a selection of logs they are allowed to access, with links to browse or search the most recent filtered log entries or, when allowed, to request access to unfiltered logs subject to approval.

*For brevity, only a high-level description of the web interface is provided for this example.*

Approval requests are queued for processing in a web form that provides basic information:

*   The reason access is requested, including specifics such as customer issue ticket numbers
*   The scope of access requested (typically a specific user account or IP address)

Approval requests trigger automated emails sent to approvers with a link to the web app page to review these requests. When each decision is taken, an email notifies the requester with the following:

*   An approval or denial
*   Reason for denial, if applicable
*   Time window for approved access

Filtered and unfiltered logs are visible on a page corresponding to each log. Queries may be entered specifying which log entries to view. An empty query shows the most recent entries with Next/Previous links for paging through the results.

Queries specify log entry fields and values, combined with Boolean operators to select matching log entries. Most recent first is the default order, unless an explicit ordering is given in the query. *For brevity, the details of query syntax are omitted.*

Filtered logs are displayed with symbolic identifiers (see Section 2.3) instead of the raw log contents. Queries may use symbolic identifiers present in filtered log content; for example, if a filtered log entry shows the IP address `US1`, a query of `[IP = US1]` would find other logs from that IP address without disclosing the address itself.

**Queries over filtered logs must disallow searches on filtered fields with exact values. For example, even if IP addresses are not shown, if the user can guess `[IP = 1.1.1.1]` (and so forth) they may eventually hit a log entry that will show it as something like `USA888` and then be able to infer the actual value.**

Even when unfiltered access is approved, users must select an option to begin unfiltered viewing and querying. **Best practice maximizes use of filtered logs, only revealing filtered values on an as-needed basis, and it is important that the user interface encourage this.**

Users can renounce the right to unfiltered log access when the task is completed. The user interface should promote this after a period of inactivity to minimize risk of unnecessary access.

**Web pages displaying log contents should not be locally cached by user agents to avoid inadvertent disclosure and to ensure that, on expiry, the log data is no longer available.**

## Section 8 – Technical Design

The Logger Recorder service consists of a write-only interface for applications to stream log event data that will be written to persistent storage, and a query interface to get views of those logs. Storage is a sequence of write-append files consisting of UTF-8 lines of text, with one line per log event. Log data as described by the relevant schema (see above) maps to/from a canonical representation as text. *Details of formatting are omitted for this example.*

**Log data fields subject to filtering should be stored in the filtered representation in addition to the raw data encrypted with an AES key generated by the service, using a new key every day. Use a hardware key storage or suitable means of securely protecting these keys.**

Since exhausting available storage represents a fatal error for a logging service, the write rate is measured against free space (`free_storage_MB` / `avg_logging_MB_per_hour`) and a priority operational alert is raised if space for fewer than 10 hours of data, assuming constant write volumes, remains (this number of hours to alert is configurable).

For performance, consider a SQL database recording filtered log event information (timestamp, log type, filename, and offset), supplementing the actual log files for efficient access.

Filtered logs hide private data with symbolic identifiers (for example, `US1` for an IP address in the US). **To avoid storing unfiltered private data, these maps go from a secure digest of the unfiltered data value to the filtered moniker.** This mapping is temporary and maintained by Logger Viewer separately for each user context per log. Users have the ability to clear mappings for a fresh start, or after 24 hours of non-use, they are automatically cleared to prevent useless buildup over time.

## Section 9 – Configuration

Log retention is configured as follows. **Data is automatically, securely, and permanently deleted beyond the retention period (not just moved to trash; use the `shred(1)` command or similar).**

```json
Retention: {
  "Log1": {"days": 10},
  "Log2": {"hours": 24},
}
```

Log access is granted by configuring lists of authorized users:
