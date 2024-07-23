# AWS-Cloud-Resume-Challenge

### Overview of the Project

The Cloud Resume Challenge (CRC) is hands-on project designed by *Forrest Brazeal*, an a Solutions Architect and AWS hero, to help individuals demonstrate their cloud skills. This challenge involves building and deploying a professional resume website using a variety of AWS services, infrastructure as code (IaC) , and CI/CD practices.

#### Project Objectives

The primary goal of the Cloud Resume Challenge is to create a serverless web application that displays a personal resume and includes a visitor counter. Generally, using and implementing:

- **AWS Services:** S3 for static website hosting, CloudFront for content delivery, Route 53 for DNS management, Lambda to update DynamoDB table, DynamoDB to store visitor count, API Gateway to trigger lambda, and Certificate Manager for SSL certificate.
- **Infrastructure as Code:** used Terraform to automate the provisioning of all AWS services.
- **CI/CD:** Implemented GitHub Actions to automate the deployment process.

#### Key Features

- **Static Website Hosting:** The resume website is hosted on AWS S3 and delivered globally via CloudFront, ensuring high availability and low latency.
- **Custom Domain and SSL:** The website is accessible via a custom domain (jote.dev) purchased from Namecheap, secured with an SSL certificate provided by AWS Certificate Manager.
- **Visitor Counter:** The website includes a visitor counter implemented using JavaScript and API Gateway. The counter updates dynamically by invoking a Lambda function that interacts with a DynamoDB table to store, update and retrieve the visitor count.
- **Automation:** The deployment of the website files, Lambda functions, and infrastructure is automated using GitHub Actions and Terraform, enabling continuous integration and delivery.

### Key Steps followed

1. **Designed the overall system:**
    After drafting on a piece of paper, I drew the following diagram on ([draw.io] (https://draw.io))
        ![CRC drawio(1)](https://github.com/user-attachments/assets/bbe2f656-a627-4ae0-b3af-3b3a01699f16)

2. **Provisioning AWS services using Terraform:**
    Wrote HCL code on main.tf and provisioned all the services required, extensively used the ([Terraform documentation / registry](https://registry.terraform.io/providers/hashicorp/aws/latest/docs)) when writing, also used VS Code Terraform Extension.

3. **Writing HTML and CSS for the website**. The easiest one. 
    Then uploaded to a separate repo, so that I can manage it separately and 
    implemented github action to update the S3 bucket created for the website hosting
    ([Github repo for  website files](<https://github.com/amanuelararso/website-files-for-AWS-CRC)>))

4. **Python code for lambda**:
    I used boto3 library to write a code to update a count on DynamoDB table called 'visitorCount'. The code returns a response code of 200 for successfull run and a body consisting of {'visitor_count': new_count} as a JSON.
    There is a separate repo for this code also and upon push to the repo, the code inside the lambda function is automatically updated. This is done using Github Action. 
    ([lambda code repo](https://github.com/amanuelararso/lambda-code-for-AWS-CRC))

5. **Configuring AWS services**:
    Requested a public **SSL certificate using Certificate Manager** for jote.dev using RSA 2048 Key Algorithm
    Created **GET method for API Gateway** and enabled CORS, so that the website gets the response it needs. And ofcourse, deployed the API on 'prod' stage.
    Created **'A' record** for *jote.dev* hosted zone in **Route 53**, a third record in addition to NS and SOA

I really enjoyed doing this project and I believe I will continue on other projects of CRC like the kubernettes, azure and terraform challenges.
