# DataSync task creation statuses<a name="understand-task-creation-statuses"></a>

When you create an AWS DataSync task, there are statuses to help you understand if the task is ready to run or having an issue\.


| Console status | API status | Description | 
| --- | --- | --- | 
|  Creating  |  `CREATING`  |  Depending on the locations in your task, you might see this status\. For example, this status displays while DataSync mounts your Network File System \(NFS\) or Server Message Block \(SMB\) server to make sure it can connect with your location\. \(Note: DataSync mounts your server again once you run the task and unmounts it once the task completes\.\) If a task is in this state for more than a few minutes, your agent might be having mounting issues that are often caused by a misconfigured firewall or mistyped NFS or SMB server hostname\. To understand the issue, check the response elements `ErrorCode` and `ErrorDetail` that are returned with the [DescribeTask](https://docs.aws.amazon.com/datasync/latest/userguide/API_DescribeTask.html#DataSync-DescribeTask-response-ErrorCode) operation\. You can also see [Troubleshooting AWS DataSync issues](troubleshooting-datasync.md)\.  | 
| Available |  `AVAILABLE`  |  The task is configured and ready to start\.  | 
| Running |  `RUNNING`  | The task is in progress\. | 
|  Unavailable  |  `UNAVAILABLE`  |  The agent that's associated with a location is offline\.  | 
|  Queued  |  `QUEUED`  |  Another task is running and using the same agent\. DataSync runs tasks in series \(first in, first out\)\. For more information, see [Queueing task executions](run-task.md#queue-task-execution)\.  | 