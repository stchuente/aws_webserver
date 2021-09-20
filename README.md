# Tools Used

I preferred to use cloudformation to setup the webserver.

# Why use cloudformation
AWS CloudFormation is an Amazon web service that lets you create, provision, and manage a collection of related Amazon services.Cloudformation support all diffrent services offer by AWS.Cloudformation is easy to use and can be customise through paramter to make it reusable.

# Linux used
* AMazon Linux 2 ami is used in this template.

# Running cloudformation from AWS UI
* Login in your AWS account.
* From AWS serive list select cloudformation.
* Now select Create Stack -> Template is ready -> Upload a template file.
* Now upload the cloduformation template that we created.
* Click Next.
* Enter Stack name of your chioce.
* Now in **Paramter** if you wish you can change VPcCidr of your choice and click on next.
* Next click on Create Stack and observer the creation events.

# Running cloudformation from AWS CLI
* First install AWS cli is it's not already present.
* To install AWS cli follow below command.
   >curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
   >unzip awscliv2.zip
   >sudo ./aws/install
* Now you can run below command to create cloudformation stack with default parameter from aws cli.
  >aws cloudformation create-stack --stack-name mywebserver --template-body file://webserver.yaml --region us-east-1 --capabilities CAPABILITY_NAMED_IAM
* To create the stack with custom paramter use below command
  >aws cloudformation create-stack --stack-name mywebserver --template-body file://webserver.yaml --parameters ParameterKey=VpcCidr,ParameterValue=10.0.0.0/24 --region us-east-1 --capabilities CAPABILITY_NAMED_IAM

# Open web page
* From Cloudformation ui select output tab and copy the url from "WebsiteURL" output block.
* Now paste the url in new tab and you should be able to see webpage open.

# Security best practices
* The webserver is placed in private subnet.
* Only http(80) and https(443) port are open.
* The loadbalancer is placed in public subnet.

