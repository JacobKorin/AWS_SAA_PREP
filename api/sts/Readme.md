## Create a new user with no permissions

We need to create a new user with no permissions and generate access keys

aws iam create-user --user-name jjtest

aws iam create-access-key --user-name jjtest --output table

## Open a second terminal and configure the cli to use the aws no permission account
aws configure access key and secret from the output in above command

## Confirm that in teminal 1 you have your original admin account and in terminal 2 you have the no permission account
aws sts get-caller-identity

## Make sure you don't have access to s3 in terminal 1

aws s3 ls

## Create a role

We need to create a role that will access a new resource

./bin/deploy

## Use new user credentials and assume role

aws iam put-user-policy \
--user-name jjtest \
--policy-name stspolicy \
--policy-document file://policy.json

aws sts assume-role \
--role-arn arn:aws:iam::268556604645:role/jacob-sts-stack-StsRole-zdB93bRufa8C \
--role-session-name s3-sts

## Configure terminal 2 with new credentials that were given when assuming role

aws configure keys from above

## Clean up

Tear down cloudformation stack using aws console

aws iam delete-user-policy --user-name jjtest --policy-name stspolicy

aws iam delete-access-key --access-key-id AKIAT5BZYSTSX3MER46T --user-name jjtest

aws iam delete-user --user-name jjtest
