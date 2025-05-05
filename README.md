# demo-alb
This repo has CFT template for ALB and GH action pipeline syntax for deployment

To deploy via github action there should be an IAM role with trusted entity policy and AWS full access to Cloud formation
Below is the policy

{
  "Effect": "Allow",
  "Principal": {
    "Federated": "arn:aws:iam::<ACCOUNT_ID>:oidc-provider/token.actions.githubusercontent.com"
  },
  "Action": "sts:AssumeRoleWithWebIdentity",
  "Condition": {
    "StringLike": {
      "token.actions.githubusercontent.com:sub": "repo:sreemural/demo-alb:ref:refs/heads/main"
    }
  }
}

For github to connect to AWS we have to create a provider in IAM and assign the role to it