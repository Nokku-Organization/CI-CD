Pipelines are written in groovy

'/' , '/* */ ' are used for commenting in groovy
println is used for printing in groovy

### pipeline-Library: 
- Library can be configured via Manage-jenkins->configure-system
- can be imported via " @Library('rep-name') "
- cleanWs() is the built in jenkins module avaiable by installing pulgin.This is used to clean the previous workspace at starting of every build.
#### step:
    dir(folder-path) 
    {
      sh pwd
    } 
  is used for changing to a required folder.
