# sdu_client_aws_lambda_s3

This AWS Lambda function updates an SDU Catalog with events that occur in an S3 bucket.

Files created, renamed, or deleted in S3 appear quickly in SDU.                

### Lambda Function

The lambda function: `sdu_client_aws_lambda_s3.py`

Runtime: `Python 3.7`

Environment Variables:

`SDU_COLLECTION_PREFIX` : `/tempZone/home/sdu/lambda`

`SDU_ENVIRONMENT_SSM_PARAMETER_NAME` :  `sdu_default_environment`

### Triggers

You must configure your lambda to trigger on all `ObjectCreated` and `ObjectRemoved` events for a connected S3 bucket.

### SDU Connection Environment

The connection information is stored in the `AWS Systems Manager > Parameter Store` as a JSON object string.

  https://console.aws.amazon.com/systems-manager/parameters

Create a parameter with:

1 - Name (must match `SDU_ENVIRONMENT_SSM_PARAMETER_NAME` above):
```
sdu_default_environment
```

2 - Description:
```
For use with SDU Client AWS Lambda S3
```

3 - Type:
```
SecureString
```

4 - Value:
```
{
    "sdu_default_resource": "s3Resc",
    "sdu_host": "sdu.example.org",
    "sdu_password": "sdu",
    "sdu_port": 1247,
    "sdu_user_name": "sdu",
    "sdu_zone_name": "tempZone"
}
```
