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

* Click on the JSON tab in the policy editor

![Click on JSON Tab](resources/IAM SelectJSONTab.png)

* Insert the code I illustrated( in below photo)  

![Writing the JSON Policy.](resources/JSONpolicycodephoto.png)

*Click Next 

![Click Next JSON Create Policy](resources/ClickNEXTJSONCREATEPOLICYEDITOR.png)


Give your policy a name and click Create Policy

![Give your IAM Policy a Name](IAMGiveNametoPolicy.png)

![Create Policy Final ](resources/IAMCreatePolicyphoto.png)

* Select Roles>

![Select Roles Options](ROLESSELECTROLESOPTIONS.png)

*Select Create Role>

![Select Initial Create Role](resources/ROLECREATEROLEINITIAL.png)



Select "Systems Manager" Use case and click Next> > 

![Select Trusted Entity and Use Case](resources/IAM rol Selected trusted entitiy and use case.png)

Give your Role a name  

![Give Your Role a Name.](resources/ROLEROLENAME.png)
  
 Click Create Role. 
  
![Click Create Role Button Photo](resources/ROLECreaterolephoto.png)

* Search for and select the policy name that I gave in the previous step, and click Next

![Add permissions for Role](resources/IAM ROLE PERMISSIONS POLICY ROOLE.png)

* Click on the role that you just created and copy your ARN that is located in the summary. (We are going to need the ARN to setup a future part.)
 
![Select Roles from options](resources/ROLESSELECTROLESOPTIONS.png)
  

![Copy the ARN for future use](resources/SelectActualARNphoto.png)

 
        
  For AWS Config setup:
* Select AWS Config(in the top search box AWS)

![Type AWS Config Searchbox](resources/AWSCONFIGSEARCH.png)


 *Select Rules from the left-hand options

 ![Select Rules from the options.](resources/ASWSCONFIGSELECTRULESOPTIONS.png)


*From the Specify rule type page type security group in the AWS Managed Rules search box and select the option that begins with Decription = Checks if security groups restrict incoming traffic to restricted ports............. >Select the option that appears and click Next.

![Search for specific rule](resources/AWS Config confirmation Rules Page actual one.png)


![AWS Config Specify Rule Type Page & Select AWS Managed Rule](resources/AWS Config confirmation Rules Page actual one.png)
 

 * Type a name to give the newly created rule in the details section


![Type name for newly created rule](resources/AWSCONFIGRULESDETAILSGIVENAME.png)
   
*Set Frequencey to 1 hour in Evaluation Mode. Click Next Near the bottom.


![Change Frequencey Recording Mode to 1 hour](resources/AWSCongfigurationRulesEditRuleFrequencyPage.png)

* Click next at the bottom of the page

 
 ![Click Next Bottom of Page](resources/AWSConfigConfigrulenext.png)


* Select Save at the bottom of the Review and Create Page. 


![Click Save at the bottom of Review and Create Page.](resources/AWSCONFIGeview and createsave.png)

*  Go back to the Rules Page and select the Rule that You Just Created(Select circle to left of the crossed-out name.)

*  ![Select the rule](resources/AWSCONFIGSELECTRULE.png)

*  Click the Actions Button in the top Right Corner and select Manage Remediation

  ![AWS Config Select Manage Remediation](resources/AWS Config Select Manage Remediation Photo.png)

*  On the Manage Remediation Page, Select Automatic Remediation under "Select Remediation Method." Select AWS-DisablePublicAccessForSecurityGroup under "Remediation Action Details."

* ![Select Proper Remediation Method & Action Details](resources/AWSConfigurationSelectRemediationmethodand remediationactiondetailsphoto.png)

*  Select Group ID from the "Resource ID parameter">
*
* ![SelectResource ID parameter](resources/ManageRemediationResourceID parameter.png)


*  Paste the ARN (Copied from Earlier) in the box to the right of "AutomationAssumeRole", then click Save Changes.


![Select Copied ARN into Parmeters](resources/ManageRemediationBacktopagepasteinparameterARNphoto.png)











Create the Security Groups for the AWS Configurations

*Search for and select EC2 (in the top searchbox AWS)


![Search for and Select EC2 ](resources/EC2SELECTFORSECURITYGROUP.png)


*Select Security Group from the left options bar

 ![Select Security Group from EC2 options](resources/SECURITYGROUPSELECTSECURITYGROUPFROMOPTIONS.png)


Select the Create Security Group Tab


![Select Create Security Group to Intialize Security Group Creation ](resources/SECURITYGROUPSELECTSECURITYGROUPFROMOPTIONS.png)



On the Create Security Groups Page, give your Security Group a name and a Description under in the "Basic Details Box">  Create 2 rules in the Inbound rules box> 

![EC2 Create Security Groups Give Your Security Group a Name](resources/SecurityGroupcreatesecuritygroupbasicdetailsphoto.pngresources/SecurityGroupcreatesecuritygroupbasicdetailsphoto.png)

Rule 1) Select SSH under type and Anywhere IPV4 under Source  
Rule 2) Select All Traffic under type and Anywhere IPV4 under Source then select Create Security Group on the bottom 

![EC2 Create Security Group Set Up Security Group Rules and Select Create Security Group Tab](resources/SecurityGroupcreatesecurityinboundruleandCREATESECURITYGROUPBUTOONphoto.png)


Create an SNS email to receive an email notification when the above rule(s) are triggered:

* Select SNS(in the top search box)

![Search SNS from AWS Searchbox](resources/SNSSearchSNS.png)
* Select Topic from the left-hand options, followed by Create Topic>

![SNS Select Topic & Create Topic Tab](resources/SNSSelecttopicandcreatetopic.png)

* On the Create Topic page, Select Standard and give your topic a name in the "Details" Section.

  ![Enter Details Part Create Topic Page](resources/Create Topic Details Page Selected Standard.png)

* Select Create topic at the bottom.


 ![Select Create Topic Button at bottom of page.](resources/SELECTCREATETOPICBUTTON.photo.png)

* Navigate to Subscriptions > Create Subscription. In the Create Subscription form, select the previously created Topic ARN from the dropdown, choose Email as the protocol, enter the desired notification email address in the Endpoint field,

* ![SNS Create Subscription Page Choose Topic ARN, Endpoint and Select Create Subscription Tab](resources/SNSCreateSubscriptioninfopage.png)

* Click Create Subscription.

![SNS Select Create Subscription](resources/SNSCreateSubscriptionSelectphoto.png)


##### Contribution Policy

This project is not accepting external contributions, including pull requests or feature requests.

It serves as a personal archive of my learning journey in applying foundational concepts in software development and version control. Active development is not ongoing, and external changes will not be integrated.

Thank you for your understanding.


    ![Another photo](resources/photo2.png)
