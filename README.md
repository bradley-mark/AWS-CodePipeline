# AWS-CodePipeline

- **End to End CI/CD service**
- **Model, visualize and automate the steps required to release your software**
- **Service to orchestrate all the DevOps components together**

**Benefits**

- Rapid Delivery
- Configurable Workflow
- Fully Managed
- Easy Integration with AWS services or Third Party Tools (Jenkins, GitHub etc)

# Deploy CloudFormation using AWS CodePipeline

Simple CloudFormation **simplets3cft.json** create S3 bucket and outputs name of bucket

![image](https://user-images.githubusercontent.com/91480603/217857715-e41934c1-b3a2-456f-b4f7-07436e5e0051.png)

# IAM - Create Service Roles

**CodePipeline role**

1. IAM Console
2. Create role
3. Trusted entity service - **AWS service** - No CodePipeline - select **EC2** to edit
4. Add permissions - **Next*
5. Role name **codepipeline_demo_service_role**
6. Change **Description** to **Allows CodePipeline...**
7. **Create role**

![image](https://user-images.githubusercontent.com/91480603/217860005-577ecb84-05c6-47df-bff1-9927fdea4dc9.png)

8. Click role
9. Click Permissions - Add permissions - Create inline policy - JSON
10. Copy/paste custome JSON policy
11. **Review policy**
12. Name **custom_codepipeline_policy_v2**
13. **Create policy**
14. **Trust relationships** **Edit Policy** change service from ec2 to codepipeline

![image](https://user-images.githubusercontent.com/91480603/217862373-9125e61e-ba92-4669-a21c-4916c8595c32.png)

15. **Update policy**
16. **Create role**

**CloudFormation role**

1. Create role
2. Trusted entity service - AWS service - **CloudFormation** **Next**
3. Add permissions - **AmazonS3FullAccess** **N ext**
4. Role name **cloudformation_s3_role**
5. **Create role**

# Configure CodePipeline


