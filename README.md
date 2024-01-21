# LambdaFn
Function code to get triggered by an S3 bucket upload and send out an SNS email notification

This code ensures that the Lambda function is triggered whenever there is an upload to an existing S3 bucket and the Lambda will find the number of words in the text file and send an email through SNS with the message, **"The word count in the file <file-name> is : number"**

## 
Here is a complete walkthrough of the project: 

[Medium Blog](https://medium.com/strategio/incoming-mail-from-aws-lambda-cf197b84a603)
