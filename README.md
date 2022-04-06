# aws-lambda-send-slack

```
#!/usr/bin/python3.9
import urllib3
import json

http = urllib3.PoolManager()

def lambda_handler(event, context):
    
    url = "<slack-webhook-url>"
    
    msg = {
        "channel": "<slack-channel>",
        "username": "AWS-LAMBDA",
        "text": event['message']
    }
    
    encoded_msg = json.dumps(msg).encode('utf-8')
    
    response = http.request('POST',url, body=encoded_msg)
    
    print({
        "message": event['message'], 
        "status_code": response.status, 
        "response": response.data
    })
    
    # return {
    #     "statusCode": response.status,
    #     "headers": {
    #         "Content-Type": "application/json"
    #     },
    #     "body": json.dumps({
    #         "message": event['message'], 
    #         #"response": response.data
    #     })
    # }
```
