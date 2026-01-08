##Create a bucket

aws s3 mb s3://jacobbucketbucket123454

## Create bucket policy

aws s3api put-bucket-policy --bucket jacobbucketbucket123454  --policy file://policy.json

## Clean up

aws s3 rm s3://jacobbucketbucket123454/*

aws s3 rb s3://jacobbucketbucket123454
