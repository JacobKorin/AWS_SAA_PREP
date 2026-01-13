## Convert to JSON

yq -o json policy.yml > policy.json

## Attach policy to no permission user

aws iam create-policy \
--policy-name jjpolicy \
--policy-document file://policy.json

aws iam attach-user-policy \
--user-name jjtest \
--policy-arn arn:aws:iam::268556604645:policy/jjpolicy
