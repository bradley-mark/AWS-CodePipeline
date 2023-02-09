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
4. Add permissions - **Next**
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
2. Trusted entity service - AWS service - **CloudFormation**
3. Add permissions - **AmazonS3FullAccess**
4. Role name **cloudformation_s3_role**
5. **Create role**

# Configure CodePipeline

1. Open CodePipeline console **https://console.aws.amazon.com/codesuite/codepipeline**
2. **Create pipeline**
3. Pipeline name **s3cft-demo-pipeline**
4. Select **Existing service role** **codepipeline_demo_role**

![image](https://user-images.githubusercontent.com/91480603/217866748-8379133e-a838-483e-8125-820bbbffea35.png)

5. Source provider - **GitHub** <Authorize Access>

![image](https://user-images.githubusercontent.com/91480603/217868829-d5aa0da5-dfeb-44fb-8466-3a5bb3ae7b24.png)
![image](https://user-images.githubusercontent.com/91480603/217869070-b290a42f-3851-44f4-a9bf-0ef847b277ff.png)

![image](https://user-images.githubusercontent.com/91480603/217869592-0ac3023f-6869-40d7-a811-2d220d8c6ac8.png)

6. Select GitHub webhooks
  
![image](https://user-images.githubusercontent.com/91480603/217869785-65393c00-8daa-4027-81fb-e0671e6e9e8c.png)

CodePipeline automatically creates the webhooks in GitHub - Any changes in GitHub will be automatically submitted to CodePipeline
  
7. **Next** Add Build stage - Skip build stage - Skip

8. Add deploy stage 

- **AWS CloudFormation**
- Action mode: **Create or update stack**
- Stack name: **s3democodepipelinestack**
- Artifact name: **SourceArtifact**
- File name: **simplets3cft.json**
- Role name: **cloudformation_s3_role**

**Next**

![image](https://user-images.githubusercontent.com/91480603/217872221-73b3c749-9982-45ff-9a55-6cf36195e62b.png)

  
