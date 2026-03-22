## Note:
In this step, we'll install and configure the CloudWatch agent on both EC2 instances to collect custom metrics.
# Reason Why?
The default EC2 metrics available in CloudWatch are limited to basic system metrics such as CPU utilization. By installing the CloudWatch agent, we can monitor critical metrics such as memory usage, disk space, and detailed system performance data, enabling comprehensive monitoring.
## Steps:
1. Connect to the Dev instance via SSH:
   ``` bash
     ssh -i your-key.pem ec2-user@dev-instance-public-ip
   ```
2. Install the CloudWatch agent:
    ``` bash
     sudo yum install amazon-cloudwatch-agent -y
   ```
3. Run the configuration wizard:
    ``` bash
     sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-config-wizard
   ```
When you run this command, you'll go through an interactive configuration process and make sure the inputs **(on Default Choice)** are as follows:

![Image ALt](https://github.com/FairuzK/Proactive-Monitoring-Security-Auto-Remediation-For-Ec2/blob/84ea6ff768ce5f4a601935c77610ab18502b75fa/Project/assets/cloudAgent.png)
