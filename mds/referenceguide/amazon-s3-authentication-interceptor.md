---
id: amazon-s3-authentication-interceptor
title: Amazon S3 authentication interceptor
sidebar_label: Amazon S3 authentication interceptor
---
#### Adds authentication for Amazon Simple Storage Service (S3) to HTTP requests.
This interceptor will provide Amazon signature 4 header authentication for Amazon Simple Storage Service. 
All single valued headers will be used for signing the request. 
The signature is added as the Authorization header.
The host header is required for usage of the Amazon REST API.
If not present already as a header this interceptor will add the following headers because they are used by Amazon to process the signed request:
x-amz-date
x-amz-content-sha256

More information on using version 4 of the signing process can be found here:
http://docs.aws.amazon.com/AmazonS3/latest/API/sig-v4-header-based-auth.html

#### Access key ID
Amazon account id

<i>Required</i>

#### Secret access key
Access key provided by Amazon

<i>Required</i>

#### Region ID
Region id of the amazon site location that will be used

<i>Required</i>

#### Service ID
Service id of the service to be used.
For Simple Storage Service this is 's3'

<i>Required</i>

