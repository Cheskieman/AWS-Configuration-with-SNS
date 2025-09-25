# Set up AWS Configuration with SNS text to be notified about any security changes to AWS Configuration.

## Full Step-by-Step guide with snapshots to describe and illustrate how AWS Config is set up with SNS text notifications.

### This project demonstrates how AWS Config is configured and how to set up SNS notifications via text message to be sent when an AWS Config rule is triggered.  In this project, we will be covering how to:
* Configure AWS Config with preinstalled rules to record all changes and to proactively enforce security actions on newly created EC2 instances
* Set up an SNS email notification to receive an email if and when an EC2 instance change takes place
  

#### Instructions on how to Remediate a Security Group that meets Non-Compliant criteria via rules set up in AWS Config


Create IAM Role to attach the remediation in AWS Config:

*Search for IAM(in the top search box AWS)
![Search IAM Searchbox](resources/IAMSearchIAM.png)

*Select Policies from the Left Hand Options

![Select Policies Options](resources/IAMClickonpolociesoptionphoto.png)

*Select Create Policy 

![IAM Create Policy Photo](resources/IAMCreatePolicyphoto.png)







* Click on the JSON tab in the policy editor>Insert the code I illustrated( in above photos)  and click Next>Give your policy a name and Click Create Policy
* Select Roles>Create Role> Select "Systems Manager" Use case and click Next> Search for and select the policy name that I gave in the previous step and click Next> Give your Role a name and click Create Role.
* Click on the role that you just created and copy your ARN that is located in the summary. (We are going to need the ARN to setup a future part.)
 
  
  ![Click JSON Tab option](resources/IAMSelectJSONTab.png)
  ![Writing the JSON Policy.](resources/JSONpolicycodephoto.png)
  ![Click Next After Creating JSON policy editor](resources/ClickNEXTJSONCREATEPOLICYEDITOR.png)
  ![Create Policy Final Photo ](resources/IAMCreatePolicyphoto.png)
  ![Selecty Roles from options](resources/ROLESSELECTROLESOPTIONS.png)
  ![Click on Create Role](resources/ROLECREATEROLE.png)
  ![Select Use Case Screen for Role.](resources/IAM role Selected trusted entity and use case.png)
  ![Add permissions for Role](resources/IAM ROLE PERMISSIONS POLICY ROOLE.png)
  ![Give Your Role a Name.](resources/ROLEROLENAME.png)
  ![Click Create Role Button Photo](resources/ROLECreaterolephoto.png)
  ![Copy the ARN for future use](resources/SelectActualARNphoto.png)

 
        
  For AWS Config setup:
* Select AWS Config(in the top search box AWS)> Select Rules from the options> From the Specify rule type page type security group in the AWS Managed Rules search box and select the option that begins with Decription = Checks if security groups restrict incoming traffic to restricted ports............. Select the option that appears and click Next.> Set Frequencey to 1 hour in Evaluation Mode.Click Next Near bottom.
*  Go back to the Rules Page and select the Rule that You Just Created> Click the Actions Button in the top Right Corner and select Manage Remediation
*  On the Manage Remediation Page, Select Automatic Remediation under "Select Remediation Method." Select AWS-DisablePublicAccessForSecurityGroup under "Remediation Action Details." Select Group ID from the "Resource ID parameter"> Paste the ARN (Copied from Earlier) in the box to the right of "AutomationAssumeRole", then click Save Changes.

![Type AWS Config Searchbox](resources/AWSCONFIGSEARCH.png)
![Another photo](resources/photo2.png)
![Search for specific rule](resources/AWS Config confirmation Rules Page actual one.png)
![AWS Config Specify Rule Type Page & Select AWS Managed Rule](resources/AWS Config confirmation Rules Page actual one.png)
![Set Recording Method and Frequency AWS Config](resources/AWS CONFIG RECORDING Setting PAGE.png)
![Change Frequencey Recording Mode to 1 hour](resources/AWSCongfigurationRulesEditRuleFrequencyPage.png)
![Click Next Bottom of Page](resources/AWSConfigConfigrulenext.png)
![Click Save at bottom of Next Page](resources/AWSCONFIGeview and createsave.png)
![AWS Config Select Manage Remediation](resources/AWS Config Select Manage Remediation Photo.png)
![Select Proper Remediation Method & Action Details](resources/AWSConfigurationSelectRemediationmethodand remediationactiondetailsphoto.png)
![SelectResource ID parameter](resources/ManageRemediationResourceID parameter.png)
![Select Copied ARN into Parmeters](resources/ManageRemediationBacktopagepasteinparameterARNphoto.png)






Create the Security Groups for the AWS Configurations

*Select EC2 (in the top searchbox AWS) Select Security Group from left options followed by selecting Create Security Group Tab> On the Create Security Groups Page give your Security Group a name and a Description under  in the "Basic Details Box">  Create 2 rules in the Inbound rules box> Rule 1) Select SSH under type and Anywhere IPV4 under Source  Rule 2) Select All Traffic under type and Anywhere IPV4 under Source then select Create Security Group on the bottom 
![EC2 Create Security Groups Give Your Security Group a Name](resources/SecurityGroupcreatesecuritygroupbasicdetailsphoto.pngresources/SecurityGroupcreatesecuritygroupbasicdetailsphoto.png)
![EC2 Create Security Group Set Up Security Group Rules and Select Create Security Group Tab](resources/SecurityGroupcreatesecurityinboundruleandCREATESECURITYGROUPBUTOONphoto.png)


Create an SNS email to receive an email notification when the above rule(s) are triggered:

* Select SNS(in the top search box)
* Select Topic from the options> On the Create Topic page, Select Standard and give your topic a name in the "Details" Section, then select Create topic at the bottom.
* Navigate to Subscriptions > Create Subscription. In the Create Subscription form, select the previously created Topic ARN from the dropdown, choose Email as the protocol, enter the desired notification email address in the Endpoint field, and click Create Subscription.
![Search SNS from AWS Searchbox](resources/SNSSearchSNS.png)
![SNS Select Create Topic Tab](resources/SNSSelecttopicandcreatetopic.png)
![Enter Details Part Create Topic Page](resources/topicdetailscreatetopicphoto.png)
![SNS Create Subscription Page Choose Topic ARN, Endpoint and Select Create Subscription Tab](resources/SNSCreateSubscriptioninfopage.png)
![SNS Select Create Subscription](resources/SNSCreateSubscriptionSelectphoto.png)


##### Contribution Policy

This project is not accepting external contributions, including pull requests or feature requests.

It serves as a personal archive of my learning journey in applying foundational concepts in software development and version control. Active development is not ongoing, and external changes will not be integrated.

Thank you for your understanding.



