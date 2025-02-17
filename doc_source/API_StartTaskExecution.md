# StartTaskExecution<a name="API_StartTaskExecution"></a>

Starts a specific invocation of a task\. A `TaskExecution` value represents an individual run of a task\. Each task can have at most one `TaskExecution` at a time\.

 `TaskExecution` has the following transition phases: INITIALIZING \| PREPARING \| TRANSFERRING \| VERIFYING \| SUCCESS/FAILURE\. 

For detailed information, see Task Execution in [Components and Terminology](https://docs.aws.amazon.com/datasync/latest/userguide/how-datasync-works.html#terminology) in the * AWS DataSync User Guide*\.

## Request Syntax<a name="API_StartTaskExecution_RequestSyntax"></a>

```
{
   "Excludes": [ 
      { 
         "FilterType": "string",
         "Value": "string"
      }
   ],
   "Includes": [ 
      { 
         "FilterType": "string",
         "Value": "string"
      }
   ],
   "OverrideOptions": { 
      "Atime": "string",
      "BytesPerSecond": number,
      "Gid": "string",
      "LogLevel": "string",
      "Mtime": "string",
      "ObjectTags": "string",
      "OverwriteMode": "string",
      "PosixPermissions": "string",
      "PreserveDeletedFiles": "string",
      "PreserveDevices": "string",
      "SecurityDescriptorCopyFlags": "string",
      "TaskQueueing": "string",
      "TransferMode": "string",
      "Uid": "string",
      "VerifyMode": "string"
   },
   "TaskArn": "string"
}
```

## Request Parameters<a name="API_StartTaskExecution_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [Excludes](#API_StartTaskExecution_RequestSyntax) **   <a name="DataSync-StartTaskExecution-request-Excludes"></a>
A list of filter rules that determines which files to exclude from a task\. The list contains a single filter string that consists of the patterns to exclude\. The patterns are delimited by "\|" \(that is, a pipe\), for example, `"/folder1|/folder2"`\.   
Type: Array of [FilterRule](API_FilterRule.md) objects  
Array Members: Minimum number of 0 items\. Maximum number of 1 item\.  
Required: No

 ** [Includes](#API_StartTaskExecution_RequestSyntax) **   <a name="DataSync-StartTaskExecution-request-Includes"></a>
A list of filter rules that determines which files to include when running a task\. The pattern should contain a single filter string that consists of the patterns to include\. The patterns are delimited by "\|" \(that is, a pipe\), for example, `"/folder1|/folder2"`\.   
   
Type: Array of [FilterRule](API_FilterRule.md) objects  
Array Members: Minimum number of 0 items\. Maximum number of 1 item\.  
Required: No

 ** [OverrideOptions](#API_StartTaskExecution_RequestSyntax) **   <a name="DataSync-StartTaskExecution-request-OverrideOptions"></a>
Represents the options that are available to control the behavior of a [StartTaskExecution](https://docs.aws.amazon.com/datasync/latest/userguide/API_StartTaskExecution.html) operation\. Behavior includes preserving metadata such as user ID \(UID\), group ID \(GID\), and file permissions, and also overwriting files in the destination, data integrity verification, and so on\.  
A task has a set of default options associated with it\. If you don't specify an option in [StartTaskExecution](https://docs.aws.amazon.com/datasync/latest/userguide/API_StartTaskExecution.html), the default value is used\. You can override the defaults options on each task execution by specifying an overriding `Options` value to [StartTaskExecution](https://docs.aws.amazon.com/datasync/latest/userguide/API_StartTaskExecution.html)\.  
Type: [Options](API_Options.md) object  
Required: No

 ** [TaskArn](#API_StartTaskExecution_RequestSyntax) **   <a name="DataSync-StartTaskExecution-request-TaskArn"></a>
The Amazon Resource Name \(ARN\) of the task to start\.  
Type: String  
Length Constraints: Maximum length of 128\.  
Pattern: `^arn:(aws|aws-cn|aws-us-gov|aws-iso|aws-iso-b):datasync:[a-z\-0-9]*:[0-9]{12}:task/task-[0-9a-f]{17}$`   
Required: Yes

## Response Syntax<a name="API_StartTaskExecution_ResponseSyntax"></a>

```
{
   "TaskExecutionArn": "string"
}
```

## Response Elements<a name="API_StartTaskExecution_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [TaskExecutionArn](#API_StartTaskExecution_ResponseSyntax) **   <a name="DataSync-StartTaskExecution-response-TaskExecutionArn"></a>
The Amazon Resource Name \(ARN\) of the specific task execution that was started\.  
Type: String  
Length Constraints: Maximum length of 128\.  
Pattern: `^arn:(aws|aws-cn|aws-us-gov|aws-iso|aws-iso-b):datasync:[a-z\-0-9]*:[0-9]{12}:task/task-[0-9a-f]{17}/execution/exec-[0-9a-f]{17}$` 

## Errors<a name="API_StartTaskExecution_Errors"></a>

For information about the errors that are common to all actions, see [Common Errors](CommonErrors.md)\.

 ** InternalException **   
This exception is thrown when an error occurs in the AWS DataSync service\.  
HTTP Status Code: 500

 ** InvalidRequestException **   
This exception is thrown when the client submits a malformed request\.  
HTTP Status Code: 400

## Examples<a name="API_StartTaskExecution_Examples"></a>

### Example<a name="API_StartTaskExecution_Example_1"></a>

The following example starts a task execution using the default options and the specified task\.

#### Sample Request<a name="API_StartTaskExecution_Example_1_Request"></a>

```
{
   "OverrideOptions": { 
      "Atime": "BEST_EFFORT",
      "BytesPerSecond": 1000,
      "Gid": "NONE",
      "Mtime": "PRESERVE",
      "PosixPermissions": "PRESERVE",
      "PreserveDevices": "NONE",
      "PreserveDeletedFiles": "PRESERVE",
      "Uid": "NONE",
      "VerifyMode": "POINT_IN_TIME_CONSISTENT"
   },
   "TaskArn": "arn:aws:datasync:us-east-2:111222333444:task/task-08de6e6697796f026" 
}
```

### Example<a name="API_StartTaskExecution_Example_2"></a>

This example illustrates one usage of StartTaskExecution\.

#### Sample Response<a name="API_StartTaskExecution_Example_2_Response"></a>

```
{
  "TaskExecutionArn": "arn:aws:datasync:us-east-2:111222333444:task/task-08de6e6697796f026/execution/exec-04ce9d516d69bd52f"
}
```

## See Also<a name="API_StartTaskExecution_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/datasync-2018-11-09/StartTaskExecution) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/datasync-2018-11-09/StartTaskExecution) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/datasync-2018-11-09/StartTaskExecution) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/datasync-2018-11-09/StartTaskExecution) 
+  [AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/datasync-2018-11-09/StartTaskExecution) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/datasync-2018-11-09/StartTaskExecution) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/datasync-2018-11-09/StartTaskExecution) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/datasync-2018-11-09/StartTaskExecution) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/datasync-2018-11-09/StartTaskExecution) 