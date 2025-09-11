# Set up AWS Configuration with SNS text to be notified about any security changes to AWS Configuration.

## Fully Step-by-Step guide with snapshots to describe and illustrate how AWS Config is set up with SNS text notifications.

### This project will display how AWS Config is set up and how to have SNS notifications via text message get sent when an AWS Config rule is triggered.  In this project, we will be covering how to:
* Configure AWS Config with preinstalled rules to record all changes and to proactively enforce security actions on newly created EC2 instances
* Set up an SNS email notification to receive an email if and when an EC2 instance change takes place
  

#### Instructions on How to............
Create an EC2 Instance
* Create the Instance Name OS & AMI
* > Select Instance Type, Key Pair & Network Settings
  > >Select Launch Instance to set up the EC2
![image alt](https://github.com/Cheskieman/AWS-Configuration-with-SNS/blob/main/Launch%20and%20Instance%20Name%20,%20Application%20OS%20AMI%20Setup.png?raw=true)
![image alt](https://github.com/Cheskieman/AWS-Configuration-with-SNS/blob/main/Launch%20An%20Instance%20Instance%20type%20Key%20Pair%20Network%20Settings.png?raw=true)
 ![image alt](https://github.com/Cheskieman/AWS-Configuration-with-SNS/blob/main/Launch%20and%20Instance%20Select%20Launch%20Instance.png?raw=true)


Create IAM Role to attach

*Search for IAM(in the top search box AWS)>Policies>Create Policy
* Click on the JSON tab in the policy editior>Insert the code I illustrated and click Next>Give your policy a name and Click Create Policy
* Select Roles>Create Role> Select "Systems Manager" Use case and Click Next> Search for and select the policy name that I gave in the previous step and click Next> Give your Role a name and click Create Role.
* Now Click on the role that you just created and copy your ARN that is located in the summary. (We are going to need the ARN to setup a future part.)




* For AWS Config setup:
*  Select AWS Config(in the top searchbox AWS)> Select Rules from the options> From the Specify rule type page type security group in the AWS Managed Rules search box and select the option that begins with Decription = Checks if security groups restrict incoming traffic to restricted ports............. Select the option that appears and click Next.
*  In the Configure Rules Page, change the Frequency Under Evaluation Mode to 1 hour and Click Next> Click on Save on the Review and Create Page.
*  Go back to the Rules Page and select the Rule that You Just Created> Click the Actions Button in the top Right Corner and Select Manage Remediation
*  On the Manage Remediation Page Select Automatic Remediation under "Select Remediation Method" Select AWS-DisablePublicAccessForSecurityGroup under "Remediation Action Details." select Group ID from the Resource ID parameter> Paste the ARN (Copied from Earlier) in the box to the right of AutomationAssumeRole then click Save Changes.
![image alt](https://github.com/Cheskieman/AWS-Configuration-with-SNS/blob/main/AWS%20CONFIG%20RECORDING%20Setting%20PAGE.png?raw=true)
 ![image alt](https://github.com/Cheskieman/AWS-Configuration-with-SNS/blob/main/AWS%20Configuration%20Data%20Governace%20.png?raw=true)
 ![image alt](https://github.com/Cheskieman/AWS-Configuration-with-SNS/blob/main/AWS%20Configuration%20Data%20Governace%20.png?raw=true)

![image alt](https://github.com/Cheskieman/AWS-Configuration-with-SNS/blob/main/AWS%20CONFIG%20DELIVERY%20ADDRESS%20AND%20SNS%20SETTING%20PAGE.png?raw=true)
*![image alt](image url)
![image alt](https://github.com/Cheskieman/AWS-Configuration-with-SNS/blob/main/AWS%20Config%20Review%20Confirm%20.png?raw=true)

Create the Security Groups for the AWS Configurations

*Select EC2 (in the top searchbox AWS) Select Security Group from left options followed selecting by Create Security Group Tab> On the Create Security Groups Page give your Security Group a name and a Description under Security Group Name in the Basic Details Box>  Create 2 rules in the Inbound rules box Rule 1) Select SSH under type and Anywhere IPV4 under Source  Rule 2) Select All Traffic under type and Anywhere IPV4 under Source then select Create Security Group on the bottom 
##### Contribution Policy

This project is not accepting external contributions, including pull requests or feature requests.

It serves as a personal archive of my learning journey in applying foundational concepts in software development and version control. Active development is not ongoing, and external changes will not be integrated.

Thank you for your understanding.



