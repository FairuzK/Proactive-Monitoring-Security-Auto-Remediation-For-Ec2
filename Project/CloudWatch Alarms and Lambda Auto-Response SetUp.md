## Intro
In this step, we'll set up CloudWatch alarms to monitor EC2 instance health and create a Lambda function that automatically responds to alerts by tagging affected resources.
# Steps
## Step 1: Creating CloudWatch Alarms for EC2 monitoring
Setting Up a High CPU Usage Alarm
1. Navigate to the CloudWatch Console
2. In the left navigation pane, click on "Alarms".
3. Click the "Create alarm"> Click "select metric."
4. In the metrics browser:
    * Click on the "EC2" category from the list of services
    * Click "Per-Instance Metrics."
    * In the search bar, type "CPUUtilization" to filter metrics
    * Find your Dev instance in the list (you can identify it by instance ID)
    * Select the checkbox next to the CPUUtilization metric for your instance
    * Click "Select metric" at the bottom right
5. Configure the metric details:

    * Set the statistic to "Average."
    * Set the period to "1 minute."
6. Configure the conditions:

    * For "Threshold type", select "Static."
    * For "Whenever CPUUtilization is...", select "Greater than/equal to"
    * Enter "85" for the threshold value.
    * Leave default settings for additional configuration
    * Click "Next."

      
**Why this threshold?** 85% CPU utilization is generally considered high for most applications. Sustained usage at this level can cause performance issues and should be investigated.
