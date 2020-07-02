- Using codedeploy we can deploy to EC2/Lambda
- Here we can see the deployment to Lambda.
- As a part of codedeployment , created one deployment group and provided appspec.yml file(you can provide via editor also) with contents:
		version: 0.0
		# In the Resources section specify the name, alias, 
		# target version, and (optional) the current version of your AWS Lambda function. 
		Resources:
		  - MyFunction: # Replace "MyFunction" with the name of your Lambda function 
			  Type: AWS::Lambda::Function
			  Properties:
				Name: "codedeployLambda" # Specify the name of your Lambda function
				Alias: "LambdaDeploy" # Specify the alias for your Lambda function
				CurrentVersion: "1" # Specify the current version of your Lambda function
				TargetVersion: "2" # Specify the version of your Lambda function to deploy
		# (Optional) In the Hooks section, specify a validation Lambda function to run during 
		# a lifecycle event. Replace "LifeCycleEvent" with BeforeAllowTraffic
		# or AfterAllowTraffic. 

https://docs.aws.amazon.com/codedeploy/latest/userguide/deployment-steps-lambda.html
https://docs.aws.amazon.com/codedeploy/latest/userguide/application-revisions-appspec-file.html#add-appspec-file-lambda

- Already lambda with "codedeployLambda" name with 2 versions and alias "LambdaDeploy" are created. 
Note: As we know ALIAS is nothing but pointing to particular version of lambda.

- so here what codedeploy do is , if multiversions are created(here 2 versions) , it will change the pointing of Alias to new version.

- Advantages of codedeploy is :
  - we can do some validation before-traffic(before changing version) and afterAllow traffic via Lifecycle events.
  - And also we can shoft traffic according multiple-options like x-percent after y-minutes.
  - And also integarion with cloudwatchlogs,cloudwatchevents,cloudwatchmetrics is there.
    https://docs.aws.amazon.com/codedeploy/latest/userguide/monitoring-cloudwatch.html
  - Roll-back is also possible on codedeploy
  - can be used in code-pipeline
  - Most importantly, codedeploy is of no cost for deploying on EC2/Lambda but with 0.02$ per update on-premise instances
    https://aws.amazon.com/codedeploy/pricing/?nc=sn&loc=3