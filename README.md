# Project Overview

This Serverless Application project focuses on creating a scalable and secure API-based cloud infrastructure using AWS services. The architecture utilizes DynamoDB for database storage, AWS Lambda for serverless function execution, and API Gateway for managing API endpoints. Security and availability are prioritized through Route 53 for DNS management and ACM for SSL certification. The front end is hosted as a static website on S3, with CloudFront providing CDN support for improved performance and reliability.

# Purpose
The primary aim of this project is to build an efficient, serverless environment that automates API-based interactions and allows for seamless data retrieval and storage. DynamoDB serves as the backend storage with email as the partition key to interact efficiently with Lambda functions. API Gateway facilitates routing, enabling a structured setup for invoking Lambda functions. This infrastructure ensures smooth deployment and a robust API layer with HTTPS support for secure access


# Project Diagram

![Blank diagram](https://github.com/user-attachments/assets/efac46cd-8534-4ef3-82df-d80af9bd6739)


# Steps
## 1. create Dynamodb

<img width="916" alt="dynam03-done" src="https://github.com/ziad3704/Serverless-Application-raffle/blob/a2d28b2eb737c85c949dbb5e27c37e60e5788e6d/Screenshot%202025-09-06%20181608.png" />

---

 ## 2.create Lambda Function
 - Lambda Function is a serverless like dynamodb fully managed by AWS, Lambda can only run like other functions when you call/trigger it, so you pay-as-you-go, Lambda scales automatically

 - Created an IAM policy and Role for the three Lambda functions so it can access dynamodb(for db) and cloud watch(for logs)

- choose this permissions: 

  1- AmazonDynamodbfullaccess

  2- AWSlambdaDynamodbexecutionrole

  3-cloudwatchlogsfullaccess

  4-AWSlambdalambdainvocation

  5-AmazonDynamodbReadonlyaccess


-  Then created 3 Lambda Functions for apply, count, draw and give it the IAM Role then tested
  
   when create lambda functions choose the following (1-Author from scratch   2-Node.js in runtime  3-use an existing role)

    1-apply-raffle

    2-count-raffle

    3-draw-raffle

  
 - logs from lambda

 
  <img width="817" alt="before-test" src="https://github.com/ziad3704/Serverless-Application-raffle/blob/edc077d371a258b3513dfb411e6f6bdd209df6f6/Screenshot%202025-09-06%20182028.png" />


 # 3. CloudWatch
 
 - CloudWatch is a monitor service that collects and tracks metrics, you can create an alarm to send to notify or see what is the performance of the service


  <img width="960" alt="logs-raffle-apply" src="https://github.com/ziad3704/Serverless-Application-raffle/blob/0bf05884a005c91cc70af2d0ccc61237e60d5127/Screenshot%202025-09-06%20182406.png" />

  
  <img width="960" alt="logs-raffle-apply" src="https://github.com/ziad3704/Serverless-Application-raffle/blob/28cbfa3d52db57c5b4a962f6091a347160da3902/Screenshot%202025-09-06%20182438.png" />
  
  

# 4. create Route53 & HostedZone

Route53 is a web service that can perform three functions domain registration, DNS routing, and health checking

<img width="823" alt="https://github.com/user-attachments/assets/6b37357f-afa2-4958-8f6b-d70994e2dd26](https://github.com/ziad3704/Serverless-Application-raffle/blob/d9793a7ed5b8150a5379d2ffb4350e45a5e35313/Screenshot%202025-09-06%20182712.png" />


**Hostedzone**

<img width="897" alt="https://github.com/user-attachments/assets/438ef3f4-be4e-4578-809c-75548b1e5ee6](https://github.com/ziad3704/Serverless-Application-raffle/blob/d33ef842133a1ec981b89dc455492854bc348eb5/Screenshot%202025-09-06%20182920.png" />


**DNS**

<img width="953" alt="create-record-53" src="https://github.com/ziad3704/Serverless-Application-raffle/blob/8828e080695047d2d0a20e6f3891c416f3ca5c87/Screenshot%202025-09-06%20183306.png" />


# 5. API Gateway
 API Gateway is a web service for creating, publishing, maintaining, monitoring, and securing REST, HTTP, and WebSocket APIs at any scale, A Developer can create an API that can route to another service or something in 
 my own app but it has to be certificate (SSL/TLS)

<img width="953" alt="must-be-disabled-to-cont" src="https://github.com/ziad3704/Serverless-Application-raffle/blob/e9cb9b2f2724b3a4e4f111f0e33852c8e4ec7a7a/Screenshot%202025-09-06%20183450.png" />

(enable-mutual-andadd-uri)
<img width="805" alt="enable-mutual-andadd-uri" src="https://github.com/ziad3704/Serverless-Application-raffle/blob/537ce4e9354f1ee7bbf80bd510846dd012ecc648/Screenshot%202025-09-06%20183520.png" />


<img width="944" alt="to-edit-in-custom-" src="https://github.com/user-attachments/assets/bf772cf9-e5d5-43a5-90ef-21f27c6136b6" />


<img width="944" alt="to-edit-in-custom-" src="https://github.com/ziad3704/Serverless-Application-raffle/blob/dd35923d630f82e75bdc670c3bed92865cb99232/Screenshot%202025-09-06%20183544.png" />


<img width="959" alt="final-3-routes" src="https://github.com/user-attachments/assets/bf5df841-2c94-48a6-b357-a0a6dfe44d74" />


# 6. ACM

 ACM (AWS Certificate Manager) Handles the complexity of creating, storing, and renewing the Certificate Public/Private (SSL/TLS)

 <img width="846" alt="2-certifcate" src="https://github.com/user-attachments/assets/d07230b8-bde0-454a-9b35-828646f2ce5e" />
 

 <img width="865" alt="create-certfi-devopshero link" src="https://github.com/user-attachments/assets/758bdce1-d567-4bde-8fe5-16f8b7c68202" />
 

 <img width="671" alt="ca-certficate" src="https://github.com/user-attachments/assets/7051ce22-df52-4680-83bd-1bfdd5cf5f15" />
 

 <img width="399" alt="steps-certficate-on-windows" src="https://github.com/user-attachments/assets/8662a05d-4918-4db4-86ab-142f22d46cb6" />
 

 <img width="392" alt="complete-certifcate" src="https://github.com/user-attachments/assets/a27fd0b7-0d94-47cf-b0a5-d2773118495d" />
 

<img width="968" alt="browser-after-certificate" src="https://github.com/user-attachments/assets/a55304f6-cf91-4fd1-a8b1-99596cc79330" />


<img width="175" alt="certificate-import-done" src="https://github.com/user-attachments/assets/e3443949-0ed8-42e2-b24d-64be13dcd763" />


<img width="958" alt="browser-select-the-certificate" src="https://github.com/user-attachments/assets/d0c4f3a9-a5e6-4e7a-bf51-17080b281adc" />

# 7. Create S3 bucket

An S3 bucket is an object storage (files) that can host a Static website or have backup objects(files)

**Add policy**

<img width="729" alt="add-policy-to-bucket" src="https://github.com/user-attachments/assets/97064423-5495-4923-98ff-4d3f9e8a00b6" />


**to change txt file to html, I change it from VScode! how? Thinking from the thoughts of terraform🔍**

first, to link between aws and vscode by using the following code:

```bash
aws configure

```
then, wrote access key and secret access key,region and json to connect between each other

<img width="767" alt="using-vscode-to-cp-txt-to-html" src="https://github.com/user-attachments/assets/d907a4ec-0f8c-4de0-8813-edf080a8c7ed" />


<img width="956" alt="2-bucket-after-edit" src="https://github.com/user-attachments/assets/260aa72c-aa55-4f25-9974-6e01d1694bd6" />


**Edit static website hosting**

<img width="960" alt="into-static-hosting-inbucket" src="https://github.com/user-attachments/assets/3e8ef911-7a4f-4b96-b970-6cefc314f6a9" />


<img width="925" alt="open-this-url-into-static" src="https://github.com/user-attachments/assets/8ee1abda-a0a1-47f0-8df1-543418a23230" />


<img width="859" alt="pemm-ca-upload" src="https://github.com/user-attachments/assets/830fd0b7-d4b0-4d11-8c5e-95c957835bec" />

**second create bucket with the same name**

<img width="885" alt="second-create-bucket-same-name-devopshero link" src="https://github.com/user-attachments/assets/ac6ff4bb-d383-4f9b-98a2-970acccd3805" />


**added Trust to URL of S3(static website URL) and DNS to CORS in API Gateway**


<img width="883" alt="edit-in-cors" src="https://github.com/user-attachments/assets/f05f2a3a-c526-479a-996b-00a5fda74b77" />


<img width="818" alt="add-devopshero-to-cors" src="https://github.com/user-attachments/assets/d7923bde-04b9-4a2c-9768-23c25bc176dc" />


# 8. Create cloudfront

<img width="959" alt="cloudfront-name-https" src="https://github.com/user-attachments/assets/20bcde53-bb7e-48b8-8659-ffcae4b68a3b" />


<img width="959" alt="cloudfront-name-https" src="https://github.com/user-attachments/assets/64ab5e10-2dbb-4b78-9b13-5996f9f824a5" />

**cname**

<img width="928" alt="front-edit-settings-cname-and-certf" src="https://github.com/user-attachments/assets/f9107c48-6834-4b07-a38f-8fd32e0cbf98" />

**copy domain name and test the website**

<img width="945" alt="-front-cp-domain-name-and-testwebsite" src="https://github.com/user-attachments/assets/a0c33409-f274-4065-95d6-fae4b84a4808" />

**WAF**

<img width="819" alt="waf-front-choose-this" src="https://github.com/user-attachments/assets/8aadf396-6631-4f86-a904-a42f6dc13812" />

----

# So The Final Results:

 **Apply to the raffle**

<img width="959" alt="check-website-devopshero link-only(apply)" src="https://github.com/user-attachments/assets/0dd102f6-2711-4d7c-ab6c-f0543e3e817d" />

---

**draw**

<img width="960" alt="check-website-draw htmlll" src="https://github.com/user-attachments/assets/a49814e7-c983-4368-9941-ca679d2d50ff" />

---


add another fake person

<img width="871" alt="add-another-fake-person" src="https://github.com/user-attachments/assets/eff26f4a-5478-401f-a024-10a6693e4d5e" />

---

# Finally Winners,

<img width="944" alt="finally-winners!!" src="https://github.com/user-attachments/assets/cb6fd0d1-2298-4a55-b3b8-6f6c86f43685" />



# **Done..!**












