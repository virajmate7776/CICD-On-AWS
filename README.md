

# CI/CD Pipeline Project On AWS

<br>
<br>
<br> 


### What is CodeCommit?
  
 <br>
 
   CodeCommit is a managed source control service by AWS that allows users to store, manage, and version their source code and artifacts securely and at scale. It supports Git, integrates with other AWS services, enables collaboration through branch and merge workflows, and provides audit logs and compliance reports to meet regulatory requirements and track changes. Overall, CodeCommit provides developers with a reliable and efficient way to manage their codebase and set up a CI/CD pipeline for their software development projects.





### Step-01:

<br>

  Set up a code repository on CodeCommit and clone it on your local.
    Log in to the AWS Management Console and navigate to CodeCommit.
    Name the repository and click on Create repository.







 


   We need to setup Git Credentials in your AWS IAM.
   Go to IAM console

   Click on Users in the left-hand menu, and then click on your user name.

 



  Scroll down to the Security credentials section.

 


Under security credentials, scroll down and come to 'HTTPS Git credentials for AWS       CodeCommit' section, click on 'Generate credentials’.













 


  Git credentials is created.
     

   Use those credentials in your local and then clone the repository from CodeCommit
In Code Commit, Go inside your repository that you created in above steps, in      right-hand side click on 'Clone URL' and choose 'Clone HTTPS'.






 


Open a terminal on your local machine.
Navigate to the directory where you want to clone the repository.

  Run the following command:
   
    git clone <your-codecommit-repo-clone-https-url>

You will be prompted to enter your Git credentials. Enter the username and password that you downloaded earlier.












 


Now we have set up a CodeCommit repository and cloned it on your local machine using Git Credentials in AWS IAM. (Note: Your user has aws codecommit permission to perform this action)













 



 

### Step-02 :

<br>

Add a new file from local and commit to your local branch
Create a new file in the local repository directory.




 

Check the status using ‘git status’ command.

 

Add the new file to your local branch using the following command:
               
    git add <filename>





 


Commit the changes to your local branch using the following command:

 

Push the local changes to CodeCommit repository.
Push the changes from your local branch to the CodeCommit repository using the following command:

      git push origin master





 


Verify that the changes have been pushed to the CodeCommit repository:

Go to the code commit repository that you created earlier, you should see the new file and content of file listed in the repository's files.


 




What is CodeBuild?
AWS CodeBuild is a fully managed build service in the cloud. CodeBuild compiles your source code, runs unit tests, and produces artifacts that are ready to deploy. CodeBuild eliminates the need to provision, manage, and scale your own build servers.


Step 1:
Create build project:
Go to the CodeBuild service. Click the "Create build project" button.

 




Fill in the details of your build project, including the project name, source provider (CodeCommit), repository, and branch.
    
In source section, select source provider AWS CodeCommit, select Repository that you created earlier and select branch master.
















 













 

In Environment section, choose operating system, runtime ad image.



















 



Step: 02
Add buildspec.yaml file to CodeCommit Repository and complete the build process.

Create a Buildspec file to build the file using an nginx server.






 


Here's what each step of the build does:

version: 0.2 specifies the version of the Buildspec syntax we're using.

phases contains the build phases for our project.

install: Installs nginx on the build environment using the apt-get package manager.

build: Copies the index.html file to the default web root directory for nginx.

post_build: Performs any additional configuration for nginx, if necessary.

artifacts: Specifies the location of the index.html file to be included in the build artifact.

Save the file and commit the changes to the repository using the git add and git    commit commands.

 

 

Push the changes to CodeCommit repository.
                             

 



 




Click "Create build project" to create your project.


 

Successfully build project is created.

Click the "Start build" button to start a new build.

          

Check the status of build in phase details section.

   Status is Succeeded.

           

To add artifacts to a CodeBuild project and store them in an S3 bucket.

Click on 'edit' and select 'Artifacts'.



     


First Create S3 bucket

 

S3 bucket is successfully created.
 
                 


                

In Artifacts, select type Amazon S3 and select bucket name that you created in above step.


 



After the build process is complete, the artifacts will be uploaded to the specified S3 bucket location.

    


Inside bucket artifact.zip folder created.











 



We can see all the files created inside folder artifacts/CodeOutput folder.

 

Click on 'index.html' file, below you can see properties of file.

Click on 'open' on right-hand side.

 



Here is an output of index.html file.















 


What is CodeDeploy?
AWS CodeDeploy is a deployment service that automates application deployments to Amazon EC2 instances, on-premises instances, serverless Lambda functions, or Amazon ECS services.

CodeDeploy can deploy application content that runs on a server and is stored in Amazon S3 buckets, GitHub repositories, or Bitbucket repositories. CodeDeploy can also deploy a serverless Lambda function. You do not need to make changes to your existing code before you can use CodeDeploy.


Step-01:
Read about Appspec.yml file for CodeDeploy.
The application specification file (AppSpec file) is a YAML -formatted or JSON-formatted file used by CodeDeploy to manage deployment. The AppSpec file for an EC2/On-Premises deployment must be named appspec. yml or appspec.yaml, unless you are performing a local deployment.






The appspec.yaml file is a configuration file that defines how the deployment should proceed. It specifies the deployment process, including which files should be deployed, where they should be deployed, and any scripts or hooks that should be executed during the deployment.

The appspec.yaml file typically includes the following sections:

version: This section specifies the version of the AppSpec file format being used.

os: This section specifies the operating system of the target instances.

files: This section specifies the source and destination locations of the files to be deployed.

hooks: This section specifies any scripts or hooks that should be executed during the deployment, such as scripts to stop and start the application.

The AppSpec file must be located in the root directory of the application source code and must be named “appspec.yml” or “appspec.yaml”. When you create a deployment group in CodeDeploy, you can specify the location of the AppSpec file in the deployment configuration.

Create a CodeDeploy application:

In CodeDeploy, go to Applications and click on 'Create application'.
Select compute platform 'EC2/on premises' and click on 'Create application'.






 


Application is successfully created.

 







Create 'service role' for enabling communication between code deploy and other aws services.

Go to IAM service and create 'code-deploy-service-role' with below permissions.

 

 





Set up an EC2 instance:
You will need to create an EC2 instance on which you want to deploy the index.html file.
Create a ubuntu EC2 instance.
       
 


Create a deployment group:
Once you have created a CodeDeploy application, you need to create a deployment group. A deployment group is a set of EC2 instances where you want to deploy your application.

 


Add deployment group name and choose 'Service role'.

 


 




 


 


We have to setup a CodeDeploy agent in order to deploy code on EC2.

  Install the CodeDeploy agent:
We need to install the CodeDeploy agent on your Ubuntu EC2 instance. The CodeDeploy agent is a software package that runs on your instance and interacts with CodeDeploy to deploy your application. You can install the CodeDeploy agent by running the following script on your EC2 instance:


 

Run the script using the command bash install.sh

        

 

 Code agent is running.




   
 


Step-02:
Add appspec.yaml file to CodeCommit Repository and complete the deployment process.
Create an appspec.yaml file:

You need to create an appspec.yaml file that tells CodeDeploy what to do with your application. Here is an appspec.yaml file that deploys the index.html file on nginx. also create 2 scripts for installing nginx and starting nginx.


 


 

 


Push all the files to code commit using 'git add' and 'git commit' commands.

 

 

Push the files to the CodeCommit repository.
All the files updated in code commit.




 




Start Build.






 

Now files are stored in s3 bucket.

 


Create deployment:

In Application, Go to Deployments and click on 'Create deployment'.




 

In revision type, select amazon S3 and paste above copied S3 url to revision location.

 


Deployment is created but events are in pending state.

 

EC2 doesn't have any role policy to retrieve the data from S3 to CodeDeploy.

So create a new service role for enabling communication between EC2 and S3, code deploy.

 

 

Add the following policies and Create role.

 

Role is created.


 

Attach that service role to EC2 instance.

Select EC2 instance, In actions, go to security and click on 'Modify IAM role'.

 

After updating IAM role, restart code-deploy agent.

  

Now Deployment status is successful.

  

All event succeeded.

 

Browse instance public IP address, it will show output of index.html file.

 

 What is CodePipeline?
CodePipeline builds, tests, and deploys your code every time there is a code           change, based on the release process models you define. Think of it as a CI/CD    Pipeline service.

Create a CodePipeline that gets the code from CodeCommit, Builds the code using CodeBuild and deploys it to a Deployment Group.
Go to the CodePipeline console. Click "Create pipeline."

 



Enter a name for your pipeline.

 


Under "Source provider," choose "AWS CodeCommit."

Select the repository and branch you want to deploy.

Click "Next."

 

Under "Build provider," choose "AWS CodeBuild."

Select "build project name."

Click "Next.

 

Under "Deploy provider," choose "AWS CodeDeploy."

Select the deployment group you created earlier.

Click "Next."

 

Review the pipeline settings and click "Create pipeline."












 

The pipeline will automatically trigger a build and deploy the new code to the EC2 instance.

Successfully created a CodePipeline that automates the deployment process.






 

Now lets make change in the code and add the new file and commit changes.

 

As soon as we make changes in code the pipeline started executing.

 



 

Browse your instance public-ip address, you can see changes got reflected and final output of index.html is displayed.









 




















