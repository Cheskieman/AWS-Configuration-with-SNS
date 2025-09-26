# Set up AWS Configuration with SNS text to be notified about any security changes to AWS Configuration.

## Full Step-by-Step guide with snapshots to describe and illustrate how AWS Config is set up with SNS text notifications.

### This project demonstrates how AWS Config is configured and how to set up SNS notifications via text message to be sent when an AWS Config rule is triggered.  In this project, we will be covering how to:
* Configure AWS Config with preinstalled rules to record all changes and to proactively enforce security actions on newly created EC2 instances
* Set up an SNS email notification to receive an email if and when an EC2 instance change takes place

####Instructions on how to Remediate a Security Group that meets Non-Compliant criteria via rules set up in AWS Config
Create IAM Role to attach the remediation in AWS Config:

Search for IAM (in the top search box AWS)

<p align="center"> <img src="resources/IAMSearchIAM.png" width="600"> </p>

Select Policies from the Left Hand Options

<p align="center"> <img src="resources/IAMClickonpolociesoptionphoto.png" width="600"> </p>

Select Create Policy

<p align="center"> <img src="resources/IAMCreatePolicyphoto.png" width="600"> </p>

Click on the JSON tab in the policy editor

<p align="center"> <img src="resources/IAMSelectJSONTab.png" width="600"> </p>

Insert the code I illustrated (in below photo)

<p align="center"> <img src="resources/JSONpolicycodephoto.png" width="600"> </p>

Click Next

<p align="center"> <img src="resources/ClickNEXTJSONCREATEPOLICYEDITOR.png" width="600"> </p>

Give your policy a name and click Create Policy

<p align="center"> <img src="resources/IAMGiveNametoPolicy.png" width="600"> </p> <p align="center"> <img src="resources/IAMCreatePolicyphoto.png" width="600"> </p>

Select Roles

<p align="center"> <img src="resources/CloickNEXTJSONCREATEPOLICYEDITOR.png" width="600"> </p>

Select Create Role

<p align="center"> <img src="resources/ROLECREATEROLEINITIAL.png" width="600"> </p>

Select "Systems Manager" Use case and click Next

<p align="center"> <img src="resources/IAMrolSelectedtrustedentityandusecase.png" width="600"> </p>

Give your Role a name

<p align="center"> <img src="resources/ROLEROLENAME.png" width="600"> </p>

Click Create Role

<p align="center"> <img src="resources/ROLECreaterolephoto.png" width="600"> </p>

Search for and select the policy name that you gave in the previous step, and click Next

<p align="center"> <img src="resources/IAMROLEPERMISSIONSPOLICYROOLE.png" width="600"> </p>

Click on the role that you just created and copy your ARN from the summary (we’ll use this later).

<p align="center"> <img src="resources/SelectActualARNphoto.png" width="600"> </p>
For AWS Config setup:

Select AWS Config (in the top search box AWS)

<p align="center"> <img src="resources/AWSCONFIGSEARCH.png" width="600"> </p>

Select Rules from the left-hand options

<p align="center"> <img src="resources/ASWSCONFIGSELECTRULESOPTIONS.png" width="600"> </p>

From the Specify rule type page, type security group in the AWS Managed Rules search box.
Select the option that begins with "Checks if security groups restrict incoming traffic to restricted ports..." and click Next.

<p align="center"> <img src="resources/AWSConfigconfirmationRulesPageactualone.png" width="600"> </p>

Type a name to give the newly created rule in the details section

<p align="center"> <img src="resources/AWSCONFIGRULESDETAILSGIVENAME.png" width="600"> </p>

Set Frequency to 1 hour in Evaluation Mode. Click Next near the bottom.

<p align="center"> <img src="resources/AWSCongfigurationRulesEditRuleFrequencyPage.png" width="600"> </p>

Click Next at the bottom of the page

<p align="center"> <img src="resources/AWSConfigConfigrulenext.png" width="600"> </p>

Select Save at the bottom of the Review and Create Page

<p align="center"> <img src="resources/AWSCONFIGreviewandcreatesave.png" width="600"> </p>

Go back to the Rules Page and select the Rule that you just created

<p align="center"> <img src="resources/AWSCONFIGSELECTRULE.png" width="600"> </p>

Click the Actions Button (top right) and select Manage Remediation

<p align="center"> <img src="resources/AWSConfigSelectManageRemediationPhoto.png" width="600"> </p>

On the Manage Remediation Page:

Select Automatic Remediation under "Select Remediation Method".

Select AWS-DisablePublicAccessForSecurityGroup under "Remediation Action Details".

<p align="center"> <img src="resources/AWSConfigurationSelectRemediationmethodandremediationactiondetailsphoto.png" width="600"> </p>

Select Group ID from the "Resource ID parameter"

<p align="center"> <img src="resources/ManageRemediationResourceIDparameter.png" width="600"> </p>

Paste the ARN (copied earlier) into "AutomationAssumeRole", then click Save Changes

<p align="center"> <img src="resources/ManageRemediationBacktopagepasteinparameterARNphoto.png" width="600"> </p>
Create the Security Groups for the AWS Configurations

Search for and select EC2 (in the top search box)

<p align="center"> <img src="resources/EC2SELECTFORSECURITYGROUP.png" width="600"> </p>

Select Security Group from the left options bar

<p align="center"> <img src="resources/SECURITYGROUPSELECTSECURITYGROUPFROMOPTIONS.png" width="600"> </p>

Select the Create Security Group tab

<p align="center"> <img src="resources/SECURITYGROUPSELECTSECURITYGROUPFROMOPTIONS.png" width="600"> </p>

On the Create Security Groups Page:

Give your Security Group a name and description under Basic Details

Create 2 rules in the Inbound rules box

<p align="center"> <img src="resources/SecurityGroupcreatesecuritygroupbasicdetailsphoto.png" width="600"> </p>

Rule 1: Select SSH under type and Anywhere IPv4 under source

Rule 2: Select All Traffic under type and Anywhere IPv4 under source

Then select Create Security Group at the bottom

<p align="center"> <img src="resources/SecurityGroupcreatesecurityinboundruleandCREATESECURITYGROUPBUTTONphoto.png" width="600"> </p>
Create an SNS email to receive notification when rules are triggered

Select SNS (in the top search box)

<p align="center"> <img src="resources/SNSSearchSNS.png" width="600"> </p>

Select Topic from the left-hand options, then Create Topic

<p align="center"> <img src="resources/SNSSelecttopicandcreatetopic.png" width="600"> </p>

On the Create Topic page:

Select Standard

Give your topic a name in the Details section

<p align="center"> <img src="resources/CreateTopicDetailsPageSelectedStandard.png" width="600"> </p>

Select Create topic at the bottom

<p align="center"> <img src="resources/SELECTCREATETOPICBUTTON.png" width="600"> </p>

Navigate to Subscriptions → Create Subscription.

Select your Topic ARN from the dropdown

Choose Email as the protocol

Enter the desired notification email in the Endpoint field

<p align="center"> <img src="resources/SNSCreateSubscriptioninfopage.png" width="600"> </p>

Click Create Subscription

<p align="center"> <img src="resources/SNSCreateSubscriptionSelectphoto.png" width="600"> </p>




##### Contribution Policy

This project is not accepting external contributions, including pull requests or feature requests.

It serves as a personal archive of my learning journey in applying foundational concepts in software development and version control. Active development is not ongoing, and external changes will not be integrated.

Thank you for your understanding.


    ![Another photo](resources/photo2.png)
