# AWS X-Ray Layer for AWS Lambda

### Compatibility
This layer is compatible for a AWS Lambda for a **x86_64** or **arm64** architectures.

### Installing
1. Download the zip file depending on the corresponding Python version.
2. Create a layer with the same Python version and choose the preferred architecture.

OR

1. Download the library by using the command inside a folder with name `python`, preferably in a Linux like system:
```pip3 install aws-xray-sdk -t .```

2. Zip the downloaded content.

3. Create a layer with the desired Python version and choose the preferred architecture. Uploading the zip.

### Documentation for using AWS X-Ray

Using this module you can patch the libraries that you use, for making the trace from their invocations. https://docs.aws.amazon.com/xray/latest/devguide/xray-sdk-python-patching.html

Example:
```
import json
import boto3
import uuid
from aws_xray_sdk.core import xray_recorder
from aws_xray_sdk.core import patch_all

patch_all()

dynamodb = boto3.client('dynamodb')

def lambda_handler(event, context):
    nombre = f"testing-{uuid.uuid4()}"
    
    dynamodb.put_item(TableName='testing', Item={'name':{'S':john},'company':{'S':'aws'}})
    
    
    return {
        'statusCode': 200,
        'body': json.dumps('Hello from Lambda! Object inserted')
    }

```