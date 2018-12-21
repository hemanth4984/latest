# latestProblem:
            The problem or challenge is when working in multiple environments with Lambda functions. Typically organizations have Development, QA and Production environments. So how would you implement new features or changes to your existing Lambda functions without impacting when one function is currently running in Production or QA?
One solution could be to have different AWS accounts but that also add some administrative overhead.
Solution:
             To solve the above problem AWS Lambda Versioning and Aliases comes into action. Using versioning in AWS Lambda, you can publish one or more versions of your Lambda function and work with different variations of your function in your development workflow, such as Development, QA or Production.
AWS Lambda also supports creating aliases for each of your Lambda function versions. Conceptually, an AWS Lambda alias is a pointer to a specific Lambda function version.
To learn more about AWS Lambda versioning and aliases check out the AWS documentation
In our example, we have a single AWS Lambda function behind AWS API Gateway. The API gateway has 2 different stages deployed named as DEV and PROD. By calling these stages you will see a different Lambda function response from a single Lambda function respectively.
This will allow us to test the API and Lambda function in DEV environment independently of Production API.
We have to do the following
Create Versions and Aliases in AWS Lambda Function
Create Dynamic Resources in AWS API Gateway
Create Deployment Stages and Variables in AWS API Gateway
Test the API
To summarize, when you call the DEV staged API endpoint the function would “Hello from Lambda World” and in case of  PROD endpoint the function would return “Hello from Lambda”
 
 

 
For Infrastructure Deployment,
Ref. CFT Code here: https://github.com/hemanth4984/latest/blob/master/api.json
Note: When we deploying the Infrastructure through Cloud Formation, the S3 Bucket and Cloud Formation is in same Region.
 



Note: We can pass parameters of the bucket name and object key in the parameters Overrides section in the cloud formation while creating code deply section in the code pipelne.


