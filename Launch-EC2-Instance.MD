**To launch the EC2 instance**

1. Open the Amazon EC2 console at [https://console.aws.amazon.com/ec2/](https://console.aws.amazon.com/ec2/). 
2. Choose **Launch Instance**. 
3. In **Step 1: Choose an Amazon Machine Image (AMI)**, find an Amazon Linux AMI at the top of the list and choose **Select**. 
4. In **Step 2: Choose an Instance Type**, choose **Next: Configure Instance Details**. 
5. In **Step 3: Configure Instance Details**, choose **Network**, and then choose the entry for your default VPC. It should look something like 

vpc-xxxxxxx (172.31.0.0/16) (default). 
    1. Choose **Subnet**, and then choose a subnet in any Availability Zone. 
    2. Choose **Next: Add Storage**. 

6. Choose **Next: Add Tags**. 
7. Name your instance and choose **Next: Configure Security Group**. 
8. In **Step 6: Configure Security Group**, review the contents of this page, ensure that **Assign a security group** is set to **Create a new security group**, and verify that the inbound rule being created has the following default values. 
    - **Type:** SSH 
    - **Protocol:** TCP 
    - **Port Range:** 22 
    - **Source:** Anywhere 0.0.0.0/0 
 
9. Choose **Review and Launch**. 
10. Choose **Launch**. 
11. Select the check box for the key pair that you created, and then choose **Launch Instances**. 
12. Choose **View Instances**. 
13. Choose the name of the instance you just created from the list, and then choose **Actions**. 
    1. From the menu that opens, choose **Networking** and then choose **Change Security Groups**. 
    2. Select the check box next to the security group with the description **default VPC security group**. 
    3. Choose **Assign Security Groups**. 

14. Choose your instance from the list. 
15. On the **Description** tab, make sure that you have two entries listed next to **security groups**—one for the default VPC security group and one for the security group that you created when you launched the instance. 
16. Make a note of the values listed next to **VPC ID** and **Public DNS**. You need those values later in this exercise.
