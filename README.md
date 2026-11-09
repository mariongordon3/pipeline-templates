# pipeline-templates

CloudFormation template for a CodePipeline that adds a manual approval stage.

Pipeline: GitHub (`java-project`) -> **Manual approval (SNS email to maintainer)** -> CodeBuild.

Deploy (us-east-1):

```
aws cloudformation create-stack --stack-name java-pipeline --region us-east-1 \
  --template-body file://pipeline-template.json --capabilities CAPABILITY_IAM \
  --parameters ParameterKey=GitHubUsername,ParameterValue=<user> \
               ParameterKey=GitHubAccessToken,ParameterValue=<token> \
               ParameterKey=MaintainerEmail,ParameterValue=<email>
```
