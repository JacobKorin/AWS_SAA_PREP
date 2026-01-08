## Create a bucket

aws s3 mb s3://jacobbucketbucket1234545

## Create a file

echo "hello world" > hello.txt
aws s3 cp hello.txt s3://jacobbucketbucket1234545 --storage-class STANDARD_IA


##Clean up
aws s3 rm s3://jacobbucketbucket1234545/hello.txt
aws s3 rb s3://jacobbucketbucket1234545
