ATS3L : Automated Tagger in S3 via Lambda

ARCHITECTURE : 
create  bucket -> create lambda function -> code in lambda handler function(read json file in s3 bucket and add tag in it ) -> deploy the code -> test the code -> 

Project Setup and Research : 

When I started building this project, the first thing I had to do was create an s3 bucket. I could have  done it manually through the AWS console, but I opted for a programmatic approach using Python and the boto3 library to make it repeatable.
To create the bucket, I referred to a few online resources and documentation for guidance , including the AWS BOT3 Documentation ( https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/s3.html )
 and blog posts by experts on Medium, such as [this step-by-step guide] ( https://medium.com/@techjunction.info/step-by-step-guide-how-to-create-an-s3-bucket-in-aws-84cfb158f405 ).
These resources were incredibly helpful in building my understanding of the overall structure before jumping into writing the actual code.


## Issues I Encountered I faced while creating the bucket. One of  the key issue was understanding the correct structure of the code.However, the biggest obstacle was my limited experience with python programming. Since boto3 relies heavily on python syntax and logic, this lack of knowledge initially made writing and debugging the code more difficult.

The next step was to add tags to the created bucket. This can also be done manually through the AWS console, but to gain a deeper understanding, I chose the programmatic approach. I wrote the code to add tags directly to the bucket using Python. It took me about a week to fully understand the structure of the program and successfully execute the code. I also made necessary changes based on specific conditions to ensure the script remains flexible and does not require future modification.

 
After adding tags programmatically, I realized that it wouldn't be efficient to manually write separate code for tagging each bucket individually. Since AWS tags follow a key–value structure, which aligns well with the JSON format, I decided to create a separate JSON file to hold all the tag data.
To implement this, I took the time to properly learn JSON — how it works, how to structure it correctly, and how to parse it in Python. Once I understood the format, I created a JSON file containing all the required tags and designed my code to read from that file. This way, tags could be added simply by uploading the JSON file into the bucket, making the process dynamic, flexible, and reusable for future buckets as well.


# code for  json file 















# the json file 


Once i upload the file in the s3 bucket now we have to add tags in s3 via AWS Lambda function. 
So next I create function in AWS Lambda console manually and then I triggered my lambda function with s3 bucket in which I add files and related 

Something like this 

The the next step is to we want 
