# Logging and Monitoring

## Site Reliability Engineering Principles
The principle underlying what should be logged and monitored are the four golden signals: latency, traffic, errors, and saturation. While each system will have additional metrics relevant to its specific use case, these four are the most critical to understanding user experience and measuring if systems are meeting business objectives.

As per Google’s SRE, the four signals can be defined as:
* Latency: The time it takes to service a request
* Traffic: A measure of how much demand is being placed on the service
* Errors: The rate of requests that fail, either explicitly (e.g., HTTP 500s), implicitly (for example, an HTTP 200 success response, but coupled with the wrong content), or by policy (for example, “If you committed to one-second response times, and request over one second is an error”)
* Saturation: How “full” is the service. A measure of your system fraction, emphasizing the resources that are most constrained

Most importantly, logging should be seen as an iterative process that evolves and improves with systems and not as a single implementation or one off fix. 

## Log Format & Best Practices

Logs should be sent as key-value pairs in string format, ideally JSON. Every log should include a timestamp with as much granularity as possible, a four-digit year, and a time zone, preferably UTC. Every log should have a unique ID, such as a trace id, and the source of the log, such as the service or file name. Logs should all be categorized according to the log4j log levels.

Logging more than less is preferred, but every log message should have a clear purpose aligned to the four signals. Information overload is a common problem with reviewing logs, and while log levels can help filter the information, a critical approach to what is logged will help prevent clutter. It is recommended to refactor in the same way code is refactored to ensure the balance between too much and too little logs is maintained.

Generally, error level logs should be done at the execution level and include stack traces for context on where the error occurred. Debug logs should be used to provide more information during the program’s execution and for understanding and debugging the entire system.

## Log Security and Governance
Sensitive data should never be included with logs. This includes information such as user emails, application keys, passwords, etc. All log forwarding should be done over encryption.

## Level-Based Logging Schema

### Default standards for all systems
* level: log4j log level
* message: message associated with the log level
* trace_id: unique ID for the event, generate at event trigger
* msec: time of the event
* service: name of the service logging the event
* host_ip: IP address of the service’s host

### User & Client Level (Browser, Mobile, Apps)
* request_method: HTTP request method
* request_uri: URI of the request, including parameters
* request_status: HTTP status of the request
* request_time: Total time to complete the HTTP request
* body_bytes_sent: Size of the request body in bytes 
If User Data Available
* user_id: The unique ID for the user

### Network & HTTP (NGINX, Varnish, Apache)
* request_method: HTTP request method
* request_uri: URI of the request, including parameters
* request_status: HTTP status of the request
* request_time: Total time to complete the HTTP request
* body_bytes_sent: Size of the request body in bytes 
* http_x_forwarded_for: Forwarder of the request

### Service & Application Level (Program Language Level)
* execution_time: Total time for the program to execute the event
* memory_util: Total memory utilization at the time of the event
* cpu_util: Total CPU utilization at the time of the event
If Service accepts HTTP requests
* request_method: HTTP request method
* request_uri: URI of the request, including parameters
* request_status: HTTP status of the request
* request_time: Total time to complete the HTTP request
* body_bytes_sent: Size of the request body in bytes 
* http_x_forwarded_for: Forwarder of the request

### Database Level (MySQL, Salesforce, DynamoDB)
Time Based Logs
* memory_util: Total memory utilization at the scheduled time
* connections: Total database connections at the scheduled time
Event specific logs based on defined thresholds (query time, max connections)
* query_time: Total time to complete the query request
* event_type: The event performed by the database

### Infrastructure Level (Linux, EC2)
Time Based Logs
* memory_util: Total memory utilization at the scheduled time
* cpu_util: Total CPU utilization at the scheduled time
* connections: Total database connections at the scheduled time
* network_io: Network utilization
* disk_io: Disk utilization

## Logging Libraries & Aggregation

It is recommended that standard, open-source libraries should be implemented on a language level for use across the Economist digital platforms. Based on the programming language and framework, a standard library can be used or a custom one can be developed. These libraries should be relatively plug and play, align to the standards above, and reduce code replication.

In the case of third-party tools and systems that do not allow implementation of standard logging libraries, a logging aggregation tool should be developed as an intermediary between the service and the centralized log parsing system.


## Context and Tracing

Logs are connected through distributed systems by passing a trace id to external calls and subroutine calls where applicable. Trace IDs are generated at the originator of the event, ie a User HTTP Request or a Database event. 

Applications should take advantage of contexts to pass the information from the event handler to subsequent tasks. Implementation will be based on the language and the application but generally:
* Middleware on the event handler should generate a trace ID if it is not present in the request/event headers or metadata
* The trace ID should be stored in the event context or assigned to a constant or session variable so that is can be retrieved at any point during the event lifecycle
* The logger should have a method to apply the trace_id to all logs
* The application should have a method to include the trace_id as a header (called X-Request-ID) or metadata in all external requests or subroutines


----
References:
https://landing.google.com/sre/book/chapters/monitoring-distributed-systems.html
https://blog.netsil.com/the-4-golden-signals-of-api-health-and-performance-in-cloud-native-applications-a6e87526e74
https://www.loggly.com/blog/30-best-practices-logging-scale/ 
https://www.owasp.org/index.php/Logging_Cheat_Sheet 
