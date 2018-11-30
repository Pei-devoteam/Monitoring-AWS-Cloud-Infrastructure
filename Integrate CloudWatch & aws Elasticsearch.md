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

