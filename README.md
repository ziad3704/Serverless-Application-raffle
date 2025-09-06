<img width="1525" height="704" alt="image" src="https://github.com/user-attachments/assets/1346e7ba-058a-4897-ba7b-6cec43f3b89c" /># Project Overview

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

<img width="823" alt="" src="https://github.com/user-attachments/assets/6b37357f-afa2-4958-8f6b-d70994e2dd26](https://github.com/ziad3704/Serverless-Application-raffle/blob/d9793a7ed5b8150a5379d2ffb4350e45a5e35313/Screenshot%202025-09-06%20182712.png" />


**Hostedzone**

<img width="897" alt="" src="https://github.com/user-attachments/assets/438ef3f4-be4e-4578-809c-75548b1e5ee6](https://github.com/ziad3704/Serverless-Application-raffle/blob/d33ef842133a1ec981b89dc455492854bc348eb5/Screenshot%202025-09-06%20182920.png" />


**DNS**

<img width="953" alt="create-record-53" src="https://github.com/ziad3704/Serverless-Application-raffle/blob/8828e080695047d2d0a20e6f3891c416f3ca5c87/Screenshot%202025-09-06%20183306.png" />


# 5. API Gateway
 API Gateway is a web service for creating, publishing, maintaining, monitoring, and securing REST, HTTP, and WebSocket APIs at any scale, A Developer can create an API that can route to another service or something in 
 my own app but it has to be certificate (SSL/TLS)

<img width="953" alt="must-be-disabled-to-cont" src="https://github.com/ziad3704/Serverless-Application-raffle/blob/e9cb9b2f2724b3a4e4f111f0e33852c8e4ec7a7a/Screenshot%202025-09-06%20183450.png" />


<img width="805" alt="enable-mutual-andadd-uri" src="https://github.com/ziad3704/Serverless-Application-raffle/blob/537ce4e9354f1ee7bbf80bd510846dd012ecc648/Screenshot%202025-09-06%20183520.png" />


<img width="944" alt="to-edit-in-custom-" src="https://github.com/ziad3704/Serverless-Application-raffle/blob/8309b069b9348ee71935b0a535d7e638de328520/Screenshot%202025-09-06%20183544.png" />


<img width="944" alt="to-edit-in-custom-" src="https://github.com/ziad3704/Serverless-Application-raffle/blob/dd35923d630f82e75bdc670c3bed92865cb99232/Screenshot%202025-09-06%20183544.png" />


<img width="959" alt="final-3-routes" src="https://github.com/ziad3704/Serverless-Application-raffle/blob/730e93f97d9b121ea6db0da6f1ccfc21d1bcbb76/Screenshot%202025-09-06%20183607.png" />


# 6. ACM

 ACM (AWS Certificate Manager) Handles the complexity of creating, storing, and renewing the Certificate Public/Private (SSL/TLS)

 <img width="846" alt="2-certifcate" src="https://github.com/ziad3704/Serverless-Application-raffle/blob/b9287912d9aeb7e9749d50696a0c0738c3412303/Screenshot%202025-09-06%20192051.png" />
 

<img width="968" alt="browser-after-certificate" src="https://github.com/ziad3704/Serverless-Application-raffle/blob/4cb22a8a82fbcd4513e73c3102cff8d9550be3ee/Screenshot%202025-09-06%20192156.png" />

<img width="865" alt="create-certfi-devopshero link" src="https://github.com/ziad3704/Serverless-Application-raffle/blob/b55e1fe483b556a1c6b45d71471611278fa03feb/Screenshot%202025-09-06%20192403.png"/>


<img width="980" alt="certificate-import-done" src="https://github.com/ziad3704/Serverless-Application-raffle/blob/c7250053577dedc885da8d087efe3d5074fbca7e/Screenshot%202025-09-06%20192403.png" />


<img width="958" alt="" src="https://github.com/ziad3704/Serverless-Application-raffle/blob/0e2a7b55841973725e795f1d9686f528ffb90a23/Screenshot%202025-09-06%20192620.png" />

# 7. Create S3 bucket

An S3 bucket is an object storage (files) that can host a Static website or have backup objects(files)

**Add policy**

<img width="729" alt="add-policy-to-bucket" src="https://github.com/ziad3704/Serverless-Application-raffle/blob/1f14597fd7af7fcd19710af9d84108df9a506010/Screenshot%202025-09-06%20195046.png" />




<img width="956" alt="2-bucket-after-edit" src="https://github.com/ziad3704/Serverless-Application-raffle/blob/8d4fcdfbbd5132b2d8bf4a20af8ef4645db1e46c/Screenshot%202025-09-06%20195128.png" />


**Edit static website hosting**

<img width="960" alt="into-static-hosting-inbucket" src="https://github.com/ziad3704/Serverless-Application-raffle/blob/bddc4da46b37c822165ec3c6808916550a7fffa1/Screenshot%202025-09-06%20195143.png" />

**public access**

<img width="885" alt="second-create-bucket-same-name-devopshero link" src="https://github.com/ziad3704/Serverless-Application-raffle/blob/a5f2f7fb9f60758973e29fa26e1feea3eebf1e4c/Screenshot%202025-09-06%20195352.png" />


**added Trust to URL of S3(static website URL) and DNS to CORS in API Gateway**


<img width="818" alt="" src="https://github.com/ziad3704/Serverless-Application-raffle/blob/c5d374de5603b256d51e576002982143833fa1fb/Screenshot%202025-09-06%20195453.png" />


# 8. Create cloudfront


<img width="819" alt="cloud_front" src="https://github.com/ziad3704/Serverless-Application-raffle/blob/d77f0e73b6111458b3a5fa8410b1cc79110d1f2c/Screenshot%202025-09-06%20200746.png" />
" />

----

# So The Final Results:

 **Apply to the raffle**

<img width="959" alt="check-website-zzye.link link-only(apply)" src="https://github.com/ziad3704/Serverless-Application-raffle/blob/a7518b85d153c7ff8791134bc2154e73bd3d135f/Screenshot%202025-09-06%20201251.png" />

---

**draw**

<img width="960" alt="check-website-draw htmlll" src="https://github.com/ziad3704/Serverless-Application-raffle/blob/a7518b85d153c7ff8791134bc2154e73bd3d135f/Screenshot%202025-09-06%20201331.png" />

---


add another fake person

<img width="871" alt="add-another-fake-person" src="https://github.com/ziad3704/Serverless-Application-raffle/blob/a7518b85d153c7ff8791134bc2154e73bd3d135f/Screenshot%202025-09-06%20201557.png" />

---

# Finally Winners,

<img width="944" alt="finally-winners!!" src="https://github.com/ziad3704/Serverless-Application-raffle/blob/a7518b85d153c7ff8791134bc2154e73bd3d135f/Screenshot%202025-09-06%20201639.png" />



# **Done..!**
































