#Create website 1

## Create a bucket

aws s3 mb s3://jacobbucketbucket12345

## Change block public access

aws s3api put-public-access-block \
--bucket jacobbucketbucket12345 \
--public-access-block-configuration "BlockPublicAcls=true,IgnorePublicAcls=true,BlockPublicPolicy=false,RestrictPublicBuckets=false"

## Create a bucket policy

aws s3api put-bucket-policy --bucket jacobbucketbucket12345 --policy file://bucket-policy.json

## Turn on static website hosting

aws s3api put-bucket-website --bucket jacobbucketbucket12345 --website-configuration file://website.json

## Upload our index.html file and include a resource that would be cross-origin

aws s3 cp index.html s3://jacobbucketbucket12345

## View website

http://jacobbucketbucket12345.s3-website.us-east-1.amazonaws.com/

# Create website 2

## Create a bucket

aws s3 mb s3://jacob2bucketbucket12345

## Change block public access

aws s3api put-public-access-block \
--bucket jacob2bucketbucket12345 \
--public-access-block-configuration "BlockPublicAcls=true,IgnorePublicAcls=true,BlockPublicPolicy=false,RestrictPublicBuckets=false"

## Create a bucket policy

aws s3api put-bucket-policy --bucket jacob2bucketbucket12345 --policy file://bucket-policy2.json

## Turn on static website hosting

aws s3api put-bucket-website --bucket jacob2bucketbucket12345 --website-configuration file://website.json

## Upload our javascript file

aws s3 cp hello.js s3://jacob2bucketbucket12345

## Set CORS on the bucket

aws s3api put-bucket-cors --bucket jacobbucketbucket12345 --cors-configuration file://cors.json
