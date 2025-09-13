<h1>🌐 Connecting Hostinger Domain to AWS Route 53 and EC2</h1>
This guide will help you connect your domain purchased from Hostinger to AWS Route 53 and then point it to an EC2 instance.


🚀 Steps
<h2 style="color:blue;">1. Create a Hosted Zone in Route 53</h2>

Go to the AWS Management Console → Route 53.

Click Hosted zones → Create hosted zone.

Enter your domain name (e.g., example.com).

Choose Public hosted zone.

Click Create.

Route 53 will generate Name Servers (NS records) like:

ns-123.awsdns-45.com
ns-678.awsdns-90.net
ns-234.awsdns-12.org
ns-345.awsdns-56.co.uk

<h3 style="color:blue;">2. Update Nameservers in Hostinger
</h3>
Log in to your Hostinger control panel
.

Go to Domains → Select your domain.

Find DNS / Nameservers settings.

Replace Hostinger’s default nameservers with the Route 53 NS records you got in Step 1.

Save changes.

⚠️ Important:

Hostinger updates may take up to 24 hours to fully propagate worldwide.

During this period, some users may still see the old nameservers while others see the new ones.

<h3 style="color:blue;">3. Get Your EC2 Public IP</h3>

Go to the EC2 Dashboard in AWS.

Select your instance → Copy the Public IPv4 address.
Example: 13.232.45.67

<h3 style="color:blue;">4. Add DNS Records in Route 53</h3>

Open your Hosted Zone in Route 53.

Click Create Record.

Add an A Record:

Record name: Leave blank (for root domain example.com) OR put www if you want www.example.com.

Record type: A – IPv4 address

Value: Your EC2 Public IP (e.g., 13.232.45.67)

TTL: 300 (default).

Save.

(Optional) Add a CNAME record for www:

Record name: www

Record type: CNAME

Value: example.com

<h3 style="color:blue;">5. Test Your Domain</h3>

Open terminal and run:

nslookup example.com


It should show your EC2’s public IP.

Open a browser → Visit http://example.com → It should load your EC2 web server.

<h3 style="color:red;">✅ Notes</h3>

Ensure EC2 Security Groups allow inbound traffic on port 80 (HTTP) and 443 (HTTPS if using SSL).

If using Elastic IP (recommended), assign it to your EC2 so your IP won’t change.

For HTTPS, use AWS Certificate Manager (ACM) or Let’s Encrypt.

Patience is key: DNS propagation delays are normal when switching from Hostinger to Route 53.
