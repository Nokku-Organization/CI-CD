using codedeploy can be useful as it has advantages and no cost but in codebuild 1/10th price difference when compared to normal-ec2-instance.

codebuild-cost evalutaion:
codebuild->cost per minute =$0.005 for 3GB Memory and 2vcpu = $0.03 per hour
normal-ec2->virginia->cost-per-cour->t2.small->2GB,2vcpu->$0.00208 per hour , if 3GB,2vcpu it is roughly $0.003 per hour
so difference of price is 1/10th , so its better to build via normal instance via installing jenkins



1)github->codedeploy(ec2,lambda,ecs)
2)github->elasticbeanstalk - https://www.youtube.com/watch?v=41vWKolYnB4
3)github->codebuild->codedeploy(ec2)
4)github->codebuild->elasticbeanstalk

for build in codebuild ->buildspec.ym file is needed
for deploy in codedeploy -> appspec.yml is needed
