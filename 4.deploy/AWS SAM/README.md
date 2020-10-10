Installation of SAM:
https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-cli-install-linux.html

Without docker also you can use for deoplying(creating/updating) lambda function.This docker is useful for local building and testing refer the bellow hello-world example documentation.Basically SAM uses docker and run containers locally and create similar environment for testing. 


This below link will give example for deployment of lambda,api-gateway using AWS SAM.
https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-getting-started-hello-world.html

Commands:

sam init #not needed if all above configuration files are present.
sam build  # make .aws-sam folder which contains all requirement-packages and application-code-files.SAM make zip file of this folder and upload to s3 bucket
sam deploy --profile sample-aws-profile 

For different parameters of sam deploy command refer link below but file "samconfig.toml" will cover the parameters and can useful for easy deployment (via jenkins)
https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/sam-cli-command-reference-sam-deploy.html



FOr Sample project refer:
https://github.com/aws-samples/cookiecutter-aws-sam-python/tree/master/%7B%7B%20cookiecutter.project_name%20%7D%7D
