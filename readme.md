# JENKINS

## TO HOST A JENKINS SERVER AND CREATE A PIPELINE THAT WILL BUILD THE APP, TEST THE APP, AND DEPLOY AN ARTIFACT.
- Pre-requirements of the machine Java, Python, Pip, Git, and Zip 

## TO SETUP AUTOMATIC BUILD TRIGGER FOR PIPELINE
- Go to Jenkins job 
- Configure Job
- Build trigger "GitHub hook trigger for GITScm polling"
- Create a pipeline script and add what is inside the Jenkinsfile

## CONFIGURE GITHUB
- On project repo settings
- Go to Webhooks and add the payload URL as http://JENKINSPUBIP:8080/github-webhook/
- Add a secret for security
- Save and check the recent deliveries to see if connection successfull, Response code: 200

## TEST
- Any commits on the repo, should automatically invoke the Pipeline/ Job

## HOW CODE WORKS
- Application source code is "app.py"
- To perform tests, we leverage the python "unitest" module and create a Python file "test_app.py" that will perform unittests on source code

####

####