# Set up AWS Configuration with SNS text to be notified about any security changes to AWS Configuration.

## Fully Step-by-Step guide with snapshots to describe and illustrate how AWS Config is set up with SNS text notifications.

### This project will display how AWS Config is set up and how to have SNS notifications via text message get sent when an AWS Config rule is triggered.  In this project, we will be covering how to:
* Create a new EC2 instance
* Set up with AWS config to record any changes to the newly created EC2 instance
* Set up an SNS text notification to receive a text if and when an EC2 instance change takes place
* Have preinstalled rules in place to configure in proactive measure specific security actions to come into effect for changes that take place to my EC2 instance(?)

#### Instructions on How to............
* Create a new EC2 Instance
>Create the Instance Name OS & AMI![image alt](https://github.com/Cheskieman/AWS-Configuration-with-SNS/blob/main/Launch%20and%20Instance%20Name%20,%20Application%20OS%20AMI%20Setup.png?raw=true)
> Select Instance Type, Key Pair & Network Settings![image alt](https://github.com/Cheskieman/AWS-Configuration-with-SNS/blob/main/Launch%20An%20Instance%20Instance%20type%20Key%20Pair%20Network%20Settings.png?raw=true)
>Select Launch Instance to set up the EC2 ![image alt](https://github.com/Cheskieman/AWS-Configuration-with-SNS/blob/main/Launch%20and%20Instance%20Select%20Launch%20Instance.png?raw=true)
* For AWS Config setup:
 > Select the Specific resource type option.! [image alt](https://github.com/Cheskieman/AWS-Configuration-with-SNS/blob/main/AWS%20CONFIG%20RECORDING%20Setting%20PAGE.png?raw=true)
 >  Select Resource Type AWS EC2 Instance and Frequencey Type Continuous! [image alt](https://github.com/Cheskieman/AWS-Configuration-with-SNS/blob/main/AWS%20Configuration%20Data%20Governace%20.png?raw=true)
 > Select under Data governance[image alt](https://github.com/Cheskieman/AWS-Configuration-with-SNS/blob/main/AWS%20Configuration%20Data%20Governace%20.png?raw=true) >Create AWS Config service Linked Role
> Under Delivery channel>Select Create a Bucket> Select checkbox for Amazon SNS topic and select Create a Topic! [image alt](https://github.com/Cheskieman/AWS-Configuration-with-SNS/blob/main/AWS%20CONFIG%20DELIVERY%20ADDRESS%20AND%20SNS%20SETTING%20PAGE.png?raw=true)
* In AWS Config Rules Page> Find Rules Searchbox type vpc-default-security-group-closed and select it as a checkbox! [image alt](https://github.com/Cheskieman/AWS-Configuration-with-SNS/blob/main/AWS%20Config%20Rules%20Page.png?raw=true)> 
* Confirm the setup of Amazon Config! [image alt](https://github.com/Cheskieman/AWS-Configuration-with-SNS/blob/main/AWS%20Config%20Review%20Confirm%20.png?raw=true)

I will document the photos and the materiel related to the SNS at a later date.

##### Contribution Policy

This project is not accepting external contributions, including pull requests or feature requests.

It serves as a personal archive of my learning journey in applying foundational concepts in software development and version control. Active development is not ongoing, and external changes will not be integrated.

Thank you for your understanding.



