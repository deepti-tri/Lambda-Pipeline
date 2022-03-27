import boto3
import os
import json
import io
import urllib.parse

s3 = boto3.client('s3')

def lambda_handler(event, context):
    
        bucket = event['Records'][0]['s3']['bucket']['name']
        key = urllib.parse.unquote_plus(event['Records'][0]['s3']['object']['key'], encoding='utf-8')
        
        response = s3.get_object(Bucket=bucket, Key=key)["Body"].read()
        
        words = response.split()
        #print('The word count in the file ', key, ' is :', len(words))
        
        TOPIC_ARN = os.environ['topicARN']
        snsClient = boto3.client('sns')
        message = io.StringIO()
        message.write('The word count in the file ' + key + ' is :' + str(len(words)))
        message.write('\n')
        response = snsClient.publish(
            TopicArn = TOPIC_ARN,
            Subject = 'Word Count Result',
            Message = message.getvalue()
        )
