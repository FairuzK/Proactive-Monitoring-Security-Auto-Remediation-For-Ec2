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
![Image Alt](https://github.com/FairuzK/Proactive-Monitoring-Security-Auto-Remediation-For-Ec2/blob/a039e6ec8ded347d2a3ead26a6e5a9baa5ae3dd5/Project/assets/cloudAgent2.png)
![Image Alt](https://github.com/FairuzK/Proactive-Monitoring-Security-Auto-Remediation-For-Ec2/blob/a039e6ec8ded347d2a3ead26a6e5a9baa5ae3dd5/Project/assets/cloudAgent3.png)
![Image Alt](https://github.com/FairuzK/Proactive-Monitoring-Security-Auto-Remediation-For-Ec2/blob/a039e6ec8ded347d2a3ead26a6e5a9baa5ae3dd5/Project/assets/cloudAgent4.png).

After completing these steps, the wizard will create a configuration file at /opt/aws/amazon-cloudwatch-agent/bin/config.json. This file contains all your metric-collection settings.

4. Start the CloudAgent

![Image Alt](https://github.com/FairuzK/Proactive-Monitoring-Security-Auto-Remediation-For-Ec2/blob/c5185d9d2ab029637703f2c4bd6cf648dd4b7808/Project/assets/cloudAgent5.png)


5. Verify the agent is running.
    ```bash
   sudo systemctl status amazon-cloudwatch-agent
    ```
    ![Image Alt](https://github.com/FairuzK/Proactive-Monitoring-Security-Auto-Remediation-For-Ec2/blob/990c1916e8f7df32f2b4a05d4228500729c5da97/Project/assets/cloudAgent6.png)


   **Expected outcome:** You should see "active (running)" in the output, confirming the agent is properly collecting and sending metrics to CloudWatch.
7. Repeat steps 1-5 for the Production instance.

**Why both instances?** We need monitoring on both environments to compare performance patterns and to ensure complete visibility across our infrastructure

