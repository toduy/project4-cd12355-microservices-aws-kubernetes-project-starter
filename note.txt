Amazon CloudWatch Observability

aws iam attach-role-policy \
--role-name EMR_EC2_DefaultRole \
--policy-arn arn:aws:iam::aws:policy/CloudWatchAgentServerPolicy

aws eks create-addon --addon-name amazon-cloudwatch-observability --cluster-name dtq-eks-project4