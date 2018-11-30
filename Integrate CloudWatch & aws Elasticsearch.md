## Step 1. Create an Amazon ES Domain
https://docs.aws.amazon.com/elasticsearch-service/latest/developerguide/es-gsg-create-domain.html

In the console, click Services, then click Elasticsearch Service to open the Amazon ES dashboard.
Click Create a new domain.
For Elasticsearch domain name, type application-logs
Click Next.
On the Configure cluster page, for Instance type, select t2.small.elasticsearch. 
Important Make sure to confirm that the selection is t2.small.elasticsearch. That is the only option which is free-tier eligible. The default selection, m4.large.elasticsearch, is not free-tier eligible.
Leave the rest of the default settings and click Next.
In the Network configuration section, select Public access.
For Set the domain access policy to, select Allow access to the domain from specific IP(s).
On the IP address pop up, type your IP address. You may look up the IP address of your computer here.
Click OK.
Scroll down and click Next.
On the Review page, scroll down and click Confirm. You should see a success message.
In the Overview tab at the bottom, you should see the Domain status as Loading. It will take about 10 minutes for the domain initialization to complete. After the initialization is complete, the Domain status changes to Active.
After the Domain status changes to Active, make a note of the Kibana URL in the Overview tab at the bottom as shown in the screenshot below.

## Step 2. Integrate Amazon CloudWatch Logs with the Amazon ES domain.
In this section, you will integrate the CloudWatch logs created in the previous exercise with the Amazon ES domain so that the logs are ingested into the Amazon ES domain. Follow the steps below.

In the console, click Services, then click CloudWatch to open the CloudWatch dashboard.
In the left side navigation menu, click Logs.
Click the radio button for the FlaskApp-Frontends-access-log log group.
Click Actions at the top.
Click Stream to Amazon Elasticsearch Service.
For Amazon ES cluster, select application-logs.
For Lambda IAM Execution Role, select Create a new IAM role. A new tab to create the IAM role should appear.
Click Allow at the bottom. The IAM role lambda_elasticsearch_execution should get populated for Lambda IAM Execution Role.
Click Next.
For Log Format, select Other.
For Subscription Filter Pattern, copy and paste the below in the text box:
[remote_addr, delimiter, remote_user, timestamp, request, status, body_bytes_sent, http_referrer, http_user_agent, http_x_forwarded_for]

The filter pattern is used to parse the logs coming from Amazon CloudWatch Logs to a tabular format with columns as specified in the pattern above. Notice that, in the log data, the logs are delimited by a '-' symbol. Refer to the screenshot below. By specifying the filter pattern, you convert the log data to a format as required by Amazon ES.

Click Test Pattern.
Click the Show test results hyperlink. You should see the log data in a tabular format.
Click Next.
On the Review & Start Streaming to Amazon Elasticsearch Service page, click Next.
Click Start Streaming.
You have successfully integrated Amazon CloudWatch Logs with the Amazon ES domain - application-logs. The logs can now be visualized in Kibana.






