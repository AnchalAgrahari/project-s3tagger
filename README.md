Automated Resource Tagging in AWS using Lambda

Problem Statement
When we use a huge amount of S3 buckets in an organisation, It becomes difficult to differentiate which project or department or cost center is contributing what amount in our aws consolidated bills.

Objective
In order to solve the problem statement, We will create multiple tags and attach it to S3 buckets.
It will help us to maintain better organization, improve searchability, and reduce manual effort.
Brainstorming:
The first thing I thought about in this project is:
How to add tags?
How to fill the knowledge gap in terms of AWS, Python, JSON?
How does it work?
Where should I start to add tags?
How to write the code?
Which programming language would be more efficient and suitable for writing the code?
Where should I learn the languages from?

Prerequisites:
Before running this project, I made sure that I have the following installed, set up or Understood.
Attribute name aise likho Tools and installation link or source info
Tools used:
Tools Name 
Function
VS code
Code editor for  the project
Python 3.12.3
Programming language used in the project
Github 
To manage code and keep track of the project
HTML
Supporting object
AWS account
To use AWS service like s3, lambda, IAM, cloudWatch 
AWS s3
To store the uploaded file 
AWS lambda
To automatically add tag on the uploaded files
IAM roles
To manage roles and permission
AWS cloudwatch
To monitor the logs of the lambda service



Reference nahi likh ke last me source likhna aur json learning ka medium pages ka bhi link dena,
Reference:
Aws boto3
https://boto3.amazonaws.com/v1/documentation/api/latest/index.html
Article for stepwise guide to create bucket 
https://medium.com/@techjunction.info/step-by-step-guide-how-to-create-an-s3-bucket-in-aws-84cfb158f405 
Guiding to create lambda function
https://medium.com/@selhorma/the-complete-beginners-guide-to-creating-an-aws-lambda-function-from-scratch-d03e6fa7e2b2


Architecture : 
Local flow of project:
Iss image me arrow poora connected hona chaiye plus flow ko 1, 2,3 krke dekho mere documents se dekh sakti ho tum. Flow tumhara galat hai, ham log file upload nhi kr rhi hain code se ham log tagg add kr rhe hain bucket me. File folder matlab object hota hai s3 me
A python file executed from terminal 
Uploaded the local file to an S3 bucket using boto3 
Adds tags to the object  ye poora bullte points hata do

AWS flow of project: isko bhi theek karo, ham log object me nhi list of bucekts me tagg add kr  rhe hian

A file uploaded to an S3 Bucket
This triggers  the AWS Lambda Function
Lambda runs the script written in python using Boto3, which applies tags to the uploaded file 
IAM roles allows Lambda to get the required permission to access S3 bucket
AWS cloudWatch records the lambda logs for monitoring and debugging
Ye bullet points hata do 
Working Process : 
First, write the code in VS code using Python and Boto3 to create an S3 bucket.
	 

Give the unique bucket name.

Check if the bucket is created in AWS S3 or not .      
   
Create a JSON file or HTML file , to upload it as an Object in the bucket (project-automated-tagging).


Upload it to an s3 bucket.




Check if the Object is uploaded to the S3 bucket.

Then create a Function in lambda





Add a trigger to the lambda function using the S3 bucket.



Write the python and boto3 script in lambda handler 


Deploy the script with deploy button in left sidebar or ctrl+shift+U

Now in the s3 bucket, re-upload the file and refresh the page .
In the bucket's properties, you’ll see the added tags.


