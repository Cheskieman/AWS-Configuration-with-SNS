# Set up AWS Configuration with SNS text to be notified about any security changes to AWS Configuration.

## Fully Step by Step guide with snapshots to describe and illustrate how AWS Config is set up with SNS text notifications.

### This project will diplay .......... In this project, we will be covering how to:
* Create a new EC2 instance
* Set up with AWS config to record any changes to newly created EC2 instance
* Set up an SNS text notification to receive a text if and when an EC2 instance change takes place
* Have preinstalled rules in place to configure in proactive measure specific security actions to come into effect for changes that take place to my EC2 instance(?)

#### Instructions on How to............
* Create a new EC2 Instance (https://github.com/Cheskieman/AWS-Configuration-with-SNS/blob/main/Launch%20and%20Instance%20Name%20,%20Application%20OS%20AMI%20Setup.png?raw=true) (https://github.com/Cheskieman/AWS-Configuration-with-SNS/blob/main/Launch%20An%20Instance%20Instance%20type%20Key%20Pair%20Network%20Settings.png?raw=true)(https://github.com/Cheskieman/AWS-Configuration-with-SNS/blob/main/Launch%20and%20Instance%20Select%20Launch%20Instance.png?raw=true) 
* In AWS Config setup> Select Specific resources type option > Select Resource Type AWS EC2 Instance and Frequencey Type Continuous> Select under Data governance Create AWS Config service Linked Role> Under Delivery channel Select Create a Bucket> Select Chrckbox for Amazon SNS topic and select Create a Topic

##### Contribution Policy

This project is not accepting external contributions, including pull requests or feature requests.

It serves as a personal archive of my learning journey in applying foundational concepts in software development and version control. Active development is not ongoing, and external changes will not be integrated.

Thank you for your understanding.



