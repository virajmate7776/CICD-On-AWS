

# CI/CD Pipeline Project On AWS

<br>
<br>

## Architecture

<br>
<br>

 ![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/4d0822d6-3170-4397-bbe9-276fc7909b90)

<br>
<br>

### What is CodeCommit?
  
 <br>
 
   CodeCommit is a managed source control service by AWS that allows users to store, manage, and version their source code and artifacts securely and at scale. It supports Git, integrates with other AWS services, enables collaboration through branch and merge workflows, and provides audit logs and compliance reports to meet regulatory requirements and track changes. Overall, CodeCommit provides developers with a reliable and efficient way to manage their codebase and set up a CI/CD pipeline for their software development projects.

<br>



### Step-01:

<br>

  Set up a code repository on CodeCommit and clone it on your local.
    Log in to the AWS Management Console and navigate to CodeCommit.
    Name the repository and click on Create repository.


![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/c3fbb18c-4820-405e-9b05-d6b8fab337aa)


<br>


 


   We need to setup Git Credentials in your AWS IAM.
   
   <br>
   
   Go to IAM console

<br>

   Click on Users in the left-hand menu, and then click on your user name.

<br>
 
 ![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/ca4903f3-5f47-460d-9769-5aa355cd41e5)


<br>

  Scroll down to the Security credentials section.

<br>

![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/5c9a1d16-ad4f-4bf6-9096-f7ed1d7ef778)

<br>

Under security credentials, scroll down and come to 'HTTPS Git credentials for AWS       CodeCommit' section, click on 'Generate credentials’.


<br>


![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/09acb7ea-c00a-477c-8127-e4dc33b6d58f)



<br>




 


  Git credentials is created.

  <br>


![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/d47c9224-0bfe-4cdc-88f3-83dda5bda06a)

<br>


   Use those credentials in your local and then clone the repository from CodeCommit

<br>

In Code Commit, Go inside your repository that you created in above steps, in right-hand side click on 'Clone URL' and choose 'Clone HTTPS'.

<br>

![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/241fa849-c3e3-4e11-a0ac-d6cb8962b97c)


<br>
 


Open a terminal on your local machine.

<br>

Navigate to the directory where you want to clone the repository.

<br>

  Run the following command:
   
    git clone <your-codecommit-repo-clone-https-url>

<br>

You will be prompted to enter your Git credentials. Enter the username and password that you downloaded earlier.

<br>



![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/4a95695e-95dd-4a40-931f-7bad07710bab)



<br>



 


Now we have set up a CodeCommit repository and cloned it on your local machine using Git Credentials in AWS IAM. (Note: Your user has aws codecommit permission to perform this action)


<br>

![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/69873950-48d0-401e-9bf7-2f53327ad7f6)

<br>
 
![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/5e23fb35-7672-499b-a729-88e56fe67809)

<br>



 

### Step-02 :

<br>

#### Add a new file from local and commit to your local branch

<br>

Create a new file in the local repository directory.

<br>

![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/90317ea9-8106-4de8-a5b9-cc4598013080)

 <br>
 

Check the status using ‘git status’ command.

 <br>
 
 ![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/251cba68-ae06-439a-b880-0a7da43e7757)

<br>


Add the new file to your local branch using the following command:
               
    git add <filename>

<br>

![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/9c36a179-0040-4767-b78f-4255581169ae)

<br>

 


Commit the changes to your local branch using the following command:

    git commit

  <br>
  
  ![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/075fe92c-d054-47ac-964d-6fb6122fa90e)

<br>


Push the local changes to CodeCommit repository.

<br>

Push the changes from your local branch to the CodeCommit repository using the following command:

    git push origin master

<br>


![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/d336b81a-bb40-4b10-b422-036ba2ab1b3a)

<br>

 


Verify that the changes have been pushed to the CodeCommit repository:

<br>

Go to the code commit repository that you created earlier, you should see the new file and content of file listed in the repository's files.

<br>
 
![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/bd506a5b-111f-46f8-818a-ec5b0e3baaa1)

<br>



### What is CodeBuild?

<br>

AWS CodeBuild is a fully managed build service in the cloud. CodeBuild compiles your source code, runs unit tests, and produces artifacts that are ready to deploy. CodeBuild eliminates the need to provision, manage, and scale your own build servers.

<br>

### Step 1:

<br>

### Create build project:

<br>

Go to the CodeBuild service. Click the "Create build project" button.

 <br>
 
 ![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/fa6540c0-75c9-410b-8272-82c351172a6f)


<br>


Fill in the details of your build project, including the project name, source provider (CodeCommit), repository, and branch.

<br>
    
In source section, select source provider AWS CodeCommit, select Repository that you created earlier and select branch master.


<br>

![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/b2491fa5-deef-4bb1-9361-70443072e82c)


<br>

![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/0f6654ad-341a-45d2-a560-8e0d2a04eec5)


<br>



In Environment section, choose operating system, runtime ad image.

<br>

![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/d97542d3-1052-4eb5-b091-d6f1a3137c76)


<br>




### Step: 02

<br>

Add buildspec.yaml file to CodeCommit Repository and complete the build process.

<br>

Create a Buildspec file to build the file using an nginx server.

<br>

![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/e40239be-058b-438f-a488-49f4b48e02f1)

<br>

Here's what each step of the build does:

<br>

**version**: 0.2 specifies the version of the Buildspec syntax we're using.

**phases** contains the build phases for our project.

<br>

**install**: Installs nginx on the build environment using the apt-get package manager.

<br>

**build**: Copies the index.html file to the default web root directory for nginx.

<br>

**post_build**: Performs any additional configuration for nginx, if necessary.

<br>

**artifacts**: Specifies the location of the index.html file to be included in the build artifact.

<br>

Save the file and commit the changes to the repository using the git add and git    commit commands.

<br>
 
![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/fd00b44c-0084-4467-9070-b3607b401cc0)

 <br>
 

Push the changes to CodeCommit repository.
                             
<br>

 
![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/85935f2f-882f-4c3b-ac00-1619d51d73f8)

 
<br>

![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/2c56c32e-ee1f-4b3b-a3ad-62288d4aa266)

<br>

Click "Create build project" to create your project.

<br>

![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/952345a2-12b3-4829-83f4-9d8bc6ea950b)
 
<br>

Successfully build project is created.

<br>

Click the "Start build" button to start a new build.

<br>

![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/7214bb25-ea24-4999-994d-b0bab3eb5ff8)

 <br>
 

Check the status of build in phase details section.

<br>

   Status is Succeeded.

<br>
   
   ![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/bb58ea08-72d9-4453-8cd0-12903f0bfa4e)
        
<br>

To add artifacts to a CodeBuild project and store them in an S3 bucket.

<br>


Click on 'edit' and select 'Artifacts'.

<br>

![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/37e8728a-24dc-47d9-973e-8aa577476a11)

<br>



First Create S3 bucket

<br>


 ![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/16fb9a83-1e2a-4692-aede-8f10bb7985ff)

<br>

S3 bucket is successfully created.
 
<br>

![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/dc93e941-d9d6-402f-bbfc-2639b381a4b9)

<br>


                

In Artifacts, select type Amazon S3 and select bucket name that you created in above step.

<br>
 
![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/73c82cc1-56d5-4306-bbfb-942d0792d2cc)

<br>

After the build process is complete, the artifacts will be uploaded to the specified S3 bucket location.

  <br>

  ![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/f0d03a29-f951-4796-be28-f8080bfeb18e)

<br>


Inside bucket artifact.zip folder created.

<br>

![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/1bddfa80-2042-4df1-98fa-56f7f882a63d)



<br>


We can see all the files created inside folder artifacts/CodeOutput folder.

<br>

![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/d6bc4c01-5a32-4e9c-92b3-31348d1ca59b)

<br>

Click on 'index.html' file, below you can see properties of file.

<br>


Click on 'open' on right-hand side.

<br> 

![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/15362f6b-155f-4ebe-b000-b5b039f98c8e)

<br>

Here is an output of index.html file.

<br>

![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/e55a3321-1d74-4877-8c81-7f8744282e3d)


<br>



### What is CodeDeploy?

<br>

AWS CodeDeploy is a deployment service that automates application deployments to Amazon EC2 instances, on-premises instances, serverless Lambda functions, or Amazon ECS services.

<br>

CodeDeploy can deploy application content that runs on a server and is stored in Amazon S3 buckets, GitHub repositories, or Bitbucket repositories. CodeDeploy can also deploy a serverless Lambda function. You do not need to make changes to your existing code before you can use CodeDeploy.

<br>


### Step-01:

<br>

Read about Appspec.yml file for CodeDeploy.

<br>

The application specification file (AppSpec file) is a YAML -formatted or JSON-formatted file used by CodeDeploy to manage deployment. The AppSpec file for an EC2/On-Premises deployment must be named appspec. yml or appspec.yaml, unless you are performing a local deployment.

<br>




The appspec.yaml file is a configuration file that defines how the deployment should proceed. It specifies the deployment process, including which files should be deployed, where they should be deployed, and any scripts or hooks that should be executed during the deployment.

<br>

The appspec.yaml file typically includes the following sections:

<br>

**version**: This section specifies the version of the AppSpec file format being used.

<br>

**os**: This section specifies the operating system of the target instances.

<br>

**files**: This section specifies the source and destination locations of the files to be deployed.

<br>

**hooks**: This section specifies any scripts or hooks that should be executed during the deployment, such as scripts to stop and start the application.

<br>

The AppSpec file must be located in the root directory of the application source code and must be named “appspec.yml” or “appspec.yaml”. When you create a deployment group in CodeDeploy, you can specify the location of the AppSpec file in the deployment configuration.


<br>

### Create a CodeDeploy application:

In CodeDeploy, go to Applications and click on 'Create application'.

<br>

Select compute platform 'EC2/on premises' and click on 'Create application'.

<br>

![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/942ec26a-1e6a-4cd1-8c97-c31a95d56495)

<br>


Application is successfully created.

<br>

![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/699a6f8d-b2fe-4b7f-b922-45fa83c6b098)

<br>



Create 'service role' for enabling communication between code deploy and other aws services.

<br>

Go to IAM service and create 'code-deploy-service-role' with below permissions.

 <br>

 ![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/76ca6a7c-5c64-4b6c-be59-e89139a1d30f)

<br>
 
![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/a23f87dc-2b30-4c7b-ae7e-070cff35886b)

<br>





Set up an EC2 instance:

<br>

You will need to create an EC2 instance on which you want to deploy the index.html file.

<br>

Create a ubuntu EC2 instance.

<br> 

![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/c6c9eee4-f8d2-472b-9ba8-0a4197480be9)

<br>

### Create a deployment group:

<br>

Once you have created a CodeDeploy application, you need to create a deployment group. A deployment group is a set of EC2 instances where you want to deploy your application.

<br>

![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/480df553-d1ba-44ac-9a08-d82ed5507e64)

<br>


Add deployment group name and choose 'Service role'.

 
<br>

 ![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/f324d002-5cc4-403c-8a17-6f44089f0116)

<br>

![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/4bcf1698-de03-4ed0-a1a8-d618159190f9)



<br>

![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/b250239d-3652-44e3-9eff-bebd261d7f71)

 
<br>

![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/787db635-6448-45a3-b61d-0e297176685f)


<br> 


We have to setup a CodeDeploy agent in order to deploy code on EC2.

<br>

 ### Install the CodeDeploy agent:

<br>

We need to install the CodeDeploy agent on your Ubuntu EC2 instance. The CodeDeploy agent is a software package that runs on your instance and interacts with CodeDeploy to deploy your application. You can install the CodeDeploy agent by running the following script on your EC2 instance:


 <br>

 ![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/4c08c513-2a25-468a-b141-62ea8a81515d)

<br>


Run the script using the command bash install.sh

   <br>

   ![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/050eeba3-19c7-4f7b-92c5-61d448e6920b)

<br>
 

 Code agent is running.

<br>

![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/d12bb8cc-c34b-489a-b97d-5841a7bba7c7)

<br>

 


### Step-02:

<br>

#### Add appspec.yaml file to CodeCommit Repository and complete the deployment process.
Create an appspec.yaml file:

<br>

You need to create an appspec.yaml file that tells CodeDeploy what to do with your application. Here is an appspec.yaml file that deploys the index.html file on nginx. also create 2 scripts for installing nginx and starting nginx.

<br>
 

![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/16b08371-b72b-4039-b8af-ba34b6492f80)

 <br>

 ![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/5f606b22-1eaf-4d8b-823c-527300502d55)

<br>

![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/9423e33a-a7a3-4198-bcbf-abb1830e6efc)

<br>

Push all the files to code commit using 'git add' and 'git commit' commands.

 <br>

 ![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/522b59ef-6b43-47cb-b34f-e366f925e462)

<br>

![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/4fd8da28-a67a-4839-8295-046dd0776d6d)

<br>

Push the files to the CodeCommit repository.

<br>

All the files updated in code commit.

<br>

![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/1c18bc84-0e44-41b3-91a2-a19f21616e21)

<br>






Start Build.


<br>

![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/940a493d-99dc-4831-a1b6-92360f43a063)

<br>
 

Now files are stored in s3 bucket.

<br>

![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/2338738d-ffc4-4479-8ca1-6dde73765476)



#### Create deployment:

<br>

In Application, Go to Deployments and click on 'Create deployment'.

<br>


![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/0b41a05d-374b-4516-a940-01616c582883)


<br>

 

In revision type, select amazon S3 and paste above copied S3 url to revision location.

 <br>


![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/fc844808-3c2c-4b28-8391-7afb87fb31d0)

<br>

Deployment is created but events are in pending state.

 <br>


 ![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/d9e4d5ec-84d4-49cc-afe6-534f96ba0ab4)


EC2 doesn't have any role policy to retrieve the data from S3 to CodeDeploy.

<br>

So create a new service role for enabling communication between EC2 and S3, code deploy.

 <br>
 

![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/d3fef948-e676-42da-a39c-1cbc04a320b5)

 <br>


![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/37fa1554-5c0c-422d-b3b9-7284af7c5733)

<br>

Add the following policies and Create role.

 <br>


 ![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/aaf11390-6aaa-47ef-bcf5-da5c6c52bc49)


Role is created.

<br>


![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/9ab14f11-3227-471e-98c4-ae33c3b07e9f)

<br>


Attach that service role to EC2 instance.

<br>

Select EC2 instance, In actions, go to security and click on 'Modify IAM role'.

<br>


![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/1aba4c4c-015b-44a9-a8f8-b6dffcb8aaa4)

<br>

After updating IAM role, restart code-deploy agent.

<br>


![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/58ce9163-bfd8-49f7-a91c-87266b26ec47)

<br>

Now Deployment status is successful.

<br>  


![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/2d44878a-0c77-409a-84ab-652cd54baadb)

<br>

All event succeeded.

<br> 

![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/4b4be7a5-e24c-4199-ae27-e9fc979ee803)

<br>

Browse instance public IP address, it will show output of index.html file.

 <br>


![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/30b68e48-eac5-4f28-9c93-5cc5c9f7b243)

<br>

 ### What is CodePipeline?
 
 <br>

CodePipeline builds, tests, and deploys your code every time there is a code change, based on the release process models you define. Think of it as a CI/CD    Pipeline service.

<br>

Create a CodePipeline that gets the code from CodeCommit, Builds the code using CodeBuild and deploys it to a Deployment Group.

<br>

Go to the CodePipeline console. Click "Create pipeline."

<br>



![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/62329d4b-94ec-4a9b-bb1b-9ae52ae67dfd)


<br>


Enter a name for your pipeline.

 <br>


 ![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/6891808a-a3f4-44f5-b8ab-c7a85f33eddb)

<br>



Under "Source provider," choose "AWS CodeCommit."

<br>

Select the repository and branch you want to deploy.

<br>

Click "Next."

 <br>


 ![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/704fe3a4-8a57-4b66-b09f-fa98f53227bc)

<br>

Under "Build provider," choose "AWS CodeBuild."

<br>

Select "build project name."

<br>


Click "Next.

 <br>


![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/473b71bf-a127-4133-be8d-aef7764b936b)

<br>

Under "Deploy provider," choose "AWS CodeDeploy."

<br>

Select the deployment group you created earlier.

<br> 

Click "Next."

 <br>


 ![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/b7b2358e-5a9f-4561-ad43-424144e07d17)

<br>



Review the pipeline settings and click "Create pipeline."


<br>


![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/167463f2-9b51-4171-8ee0-677d78f03eba)


<br>


The pipeline will automatically trigger a build and deploy the new code to the EC2 instance.

<br>

Successfully created a CodePipeline that automates the deployment process.

<br>


![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/9d9b8a2a-1460-4138-8aec-25c94c9e5b4b)


<br>
 

Now lets make change in the code and add the new file and commit changes.

 <br>


 ![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/5246d3fe-441a-4f40-bdec-2e243f045ddd)

<br>

As soon as we make changes in code the pipeline started executing.

<br>


![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/8e1a8ac7-a4f5-4874-b75a-94ac871461f5)


<br>
 

![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/be3125a2-b5d2-471f-8d3f-95c062e96dab)

<br>

Browse your instance public-ip address, you can see changes got reflected and final output of index.html is displayed.

<br>


![image](https://github.com/virajmate7776/CICD-On-AWS/assets/117629972/21bd580c-f308-440b-815d-ff5672921f3e)

<br>
<br>
