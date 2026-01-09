## Create a bucket

aws s3 mb s3://jacobbucketbucket

## Create a file 

echo "hello world" > hello.txt
aws s3 cp hello.txt s3://jacobbucketbucket

## put object with encryption of KMS

aws s3api put-object \
--bucket jacobbucketbucket \
--key hello.txt \
--body hello.txt \
--server-side-encryption "aws:kms"
--ssekms-key-id  "enter-your-kms-key-id-here"

## Put object with encryption of SSE-C

openssl rand -out ssec.key 32

aws s3 cp hello.txt s3://jacobbucketbucket/hello.txt
--sse-c AES256
--sse-c-key fileb://ssec.key

aws s3 cp s3://jacobbucketbucket/hello.txt hello.txt --sse-c AES256 --sse-c-key fileb://ssec.key
