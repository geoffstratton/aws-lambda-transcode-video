Repo Name
=========
aws-lambda-transcode-video

Description
---------------
AWS Lambda script for automatically transcoding (converting) video uploaded to an S3 bucket, using Lambda to fire an Elastic Transcoder pipeline. Uses Python (tested with 3.7), Amazon's boto3 SDK, and some S3 and Lambda triggers. 

Prerequisites
---------------
* The [boto3 SDK](https://aws.amazon.com/sdk-for-python/).
* A couple of S3 buckets for the uploaded and completed media files.
* An [Elastic Transcoder](https://aws.amazon.com/elastictranscoder/) pipeline that specifies the previously created S3 buckets for input and output.  
* The Lambda function must have an attached IAM role for starting Elastic Transcoder pipelines, and the ability to read your S3 bucket. AmazonElasticTranscoderJobsSubmitter and the s3.GetObject permission will work.
* An S3 trigger to fire the Lambda function when a file is uploaded.
* In the Lambda function, set PIPELINE_ID to your Transcoder pipeline.

### To set up boto3 for development (Amazon Linux and similar):
```
sudo yum install -y python3 python3-pip python3-setuptools
pip3 install boto3 --user
aws configure [enter your AWS access key and secret key]

python3
>>> import boto3
>>> ec2 = boto3.client('ec2')
>>> response = ec2.run_instances(ImageId='ami-00dc79254d0461090',InstanceType='t2.micro',KeyName='MY KEY',MinCount=1,MaxCount=1)
```

License
---------------
GNU General Public License v3.0
