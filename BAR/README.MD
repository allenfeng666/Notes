# Orchestrator Service
Orchestrator Service is a service that launches a scheduled automatic workflow. The goal in the first version is to send emails to a dynamic list of relationships, we want to make sure to build the service architecture to support creating generic workflows in the future.

It run on Java 17.

Integration test is not avaliable right now.

# Get to know the Orchestrator Service
![Alt text](<Overall Workflow.png>)
The Orchestrator service is managed by the Segment Manager.

### Workflow
A workflow defines the actions, a single segment, stages, and conditions that tell our outreach workflow service how to operate. Effectively it is a script that automates user actions in the Impact platform.

### Segment
A segment is a saved set of filters for a list of entities. These can be relationships, brands or partners. In regards to workflows, the segment is the scope of entities the workflow will evaluate. The list of the segment is usually dynamically generated.


### Job
This is what gets executed when a workflow is evaluated.   We call it a job and it is registered in job service.   A workflow would be the definition of what the job does.

### The orchestrator process
![Alt text](<Step by Step orchestrator process.png>)


# Where to find the logs?
https://console.cloud.google.com/kubernetes/deployment/us-east1/stage-gke-ha-use1/exp-partner-1/bar-workflow-orchestrator-springboot/logs?project=stage-infrastructure

### Sample log (Local)
```
{"message":"========================Scheduler finished========================","endOfBatch":false,"loggerFqcn":"org.apache.logging.slf4j.Log4jLogger","contextMap":{},"threadId":60,"threadPriority":5}
{"message":"Orchestrator completed in 1 second(s)","endOfBatch":false,"loggerFqcn":"org.apache.logging.slf4j.Log4jLogger","contextMap":{},"threadId":60,"threadPriority":5}
{"message":"Orchestrator started. (Schedule: every 30 sec).","endOfBatch":false,"loggerFqcn":"org.apache.logging.slf4j.Log4jLogger","contextMap":{},"threadId":60,"threadPriority":5}
{"message":"Workflow ID: 9284","endOfBatch":false,"loggerFqcn":"org.apache.logging.slf4j.Log4jLogger","contextMap":{},"threadId":60,"threadPriority":5}
{"message":"Segment ID: 1eeb5eda-9b32-6353-afe6-d7a3be93685c","endOfBatch":false,"loggerFqcn":"org.apache.logging.slf4j.Log4jLogger","contextMap":{},"threadId":60,"threadPriority":5}
{"message":"ICEE response JobID received: 1eebc887-5c7d-6ab0-a2e4-31a49e606bcb","endOfBatch":false,"loggerFqcn":"org.apache.logging.slf4j.Log4jLogger","contextMap":{},"threadId":60,"threadPriority":5}
{"message":"ICEE request sent, job ID: 1eebc887-5c7d-6ab0-a2e4-31a49e606bcb","endOfBatch":false,"loggerFqcn":"org.apache.logging.slf4j.Log4jLogger","contextMap":{},"threadId":60,"threadPriority":5}
{"message":"Email content: {\"result\":{\"evaluateSinglePartnerAdvanced\":{\"workflowId\":9284,\"workflowName\":\"test\",\"campaignId\":5280,\"segmentId\":\"11677d2c-b708-11ee-a9c5-42010a3412ac\",\"node\":1,\"partnerId\":3,\"systemWorkflow\":false,\"actions\":[{\"action\":[{\"value\":{\"content\":\"\\u003chtml\\u003e\\u003ch1\\u003ebig sale on gloves!\\u003c/h1\\u003e\\u003c/html\\u003e\",\"subject\":\"happy holidays\",\"senderName\":\"Santa\",\"replyToName\":\"  North Pole\",\"replyToEmail\":\"samson.poon@impact.com\"}}],\"actionTypeName\":\"SEND_EMAIL\",\"actionTypeDisplayName\":\"Send Email\",\"actionId\":10926}]}},\"requestType\":\"BRAND_EVALUATE_SINGLE_PARTNER_ADVANCED\",\"trigger\":\"ADVANCED_WORKFLOW\",\"dryRun\":false,\"requestId\":\"468d614e-e50f-40f5-a519-73cdb76036c5\",\"errors\":[],\"warnings\":[],\"requestTimeUtc\":\"Jan 26, 2024, 12:21:17 PM\",\"completionTimeUtc\":\"Jan 26, 2024, 12:21:17 PM\",\"success\":true}","endOfBatch":false,"loggerFqcn":"org.apache.logging.slf4j.Log4jLogger","contextMap":{},"threadId":60,"threadPriority":5}
{"message":"Time finished: 2024-01-26 12:21:17.470323","endOfBatch":false,"loggerFqcn":"org.apache.logging.slf4j.Log4jLogger","contextMap":{},"threadId":60,"threadPriority":5}
{"message":"========================Scheduler finished========================","endOfBatch":false,"loggerFqcn":"org.apache.logging.slf4j.Log4jLogger","contextMap":{},"threadId":60,"threadPriority":5}
```