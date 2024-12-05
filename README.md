# LetsDefend-Phishing-Detection

<div>
  <b>SEVERITY:</b> HIGH | <b>DATE:</b> March 22, 2021 (09:23PM) | <b>RULE NAME:</b> SOC141 - Phishing URL Detected | <b>TYPE:</b> Proxy
  <br>
  <br>
  <b>EventID:</b> 86
  <br>
  <b>Event Time:</b> Mar, 22, 2021, 09:23 PM
  <br>
  <b>Rule:</b> SOC141 - Phishing URL Detected
  <br>
  <b>Level:</b> Security Analyst
  <br>
  <b>Source Address:</b> 172.16.17.49
  <br>
  <b>Source Hostname:</b> EmilyComp
  <br>
  <b>Destination Address:</b> 91.189.114.8
  <br>
  <b>Destination Hostname:</b> mogagrocol.ru
  <br>
  <b>Username:</b> ellie
  <br>
  <b>Request URL:</b> http://mogagrocol.ru/wp-content/plugins/akismet/fv/index.php?email=ellie@letsdefend.io
  <br>
  <b>User Agent:</b> Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/79.0.3945.88 Safari/537.36
  <br>
  <b>Device Action:</b> Allowed
</div>
<br>
[Introduction: This repository showcases my work on implementing a phishing alert detection system using the Let's Defend platform. Let's Defend is an open-source Security Operations Center (SOC) platform for incident response and threat detection. In this project, I focused on detecting phishing alerts by integrating threat intelligence, analyzing suspicious emails, and leveraging automated detection mechanisms within Let's Defend. The primary goal was to identify phishing attempts in real-time by evaluating various indicators, such as Suspicious URLs and domains, Email header anomalies, Malicious attachments or links, and Behavioral analysis of phishing attempts.]
<br>
<br>
Please also use this as a guide on how to work phishing alerts using Let's Defend. For any questions or concerns you can <b>CONTACT</b> me directly on <a href= "https://www.linkedin.com/in/bradley-vilsaint-414329267/">LinkedIn</a> or email <a href="info@letsdefend.io">info@letsdefend.io</a> for support.
<br>
<br>
<b>STEP 1</b><br>
While working through this alert, it is important to keep track of what the alert has provided. <b>What should I do first?</b> Well good question. If you head to <b>"CASE PLAYBOOK"</b>, you are provided with details on what you should check for. Here is the collection data for this alert: <br><br>

* <b>Source Address:</b> 172.16.17.49<br>
* <b>Destination Address:</b> 91.189.114.8<br>
* <b>User-Agent:</b>Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/79.0.3945.88 Safari/537.36<br><br>

<b>STEP 2</b><br>
You will then search the logs for specific details within the <b>"LOG MANAGEMENT"</b> tab. But you may ask yourself <b>"What should I search for in Log Management"?</b> You are on the right track just asking yourself that question. It's okay to be curious when it comes to investigating suspicious activities. Let's pretend you are sensing your significant other may be cheating on you, and you are figuring out different ways to gather evidence to determine whether this is true or false. Within Log Management, I have searched the destination address of <b>91.189.114.8</b> as shown above and encountered two results with a source address of <b>172.16.17.49</b> linked to the sender. While also doing a little digging, I went ahead and searched the sender's IP address within the Log Management and noticed a variety of links sent to several destination addresses.<br>

<b>type:</b>
<br>
<b>source_address:</b> 172.16.17.49
<br>
<b>source_port:</b> 55662
<br>
<b>destination_address:</b> 91.189.114.8, 67.68.210.95, 162.241.242.173, 68.66.243.79, 67.199.248.11
<br>
<b>destination_port:</b> 80 / 443
<br>
<b>time:</b> Mar, 22, 2021, 09:23 PM
<br>
<b>Request URL:</b> <br><br>|DO NOT CLICK|<br> 
http://mogagrocol.ru/wp-content/plugins/akismet/fv/index.php?email=ellie@letsdefend.io
http://67.68.210.95/2SjAcA5VhhJiFjBQ/vvszin6AicmidnG5bg/DaDVVYvfEHlcIIcgcu/0U5UiIkaHankrHGa/FYSJmdQDj2ejni1UI/
http://162.241.242.173:8080/HQ9TemntfBzghL/3wz57awaSHlQrrnP/S78n2aUqY7U/
http://places.hayatistanbul.net/wp-content/themes/Netflix
<br>|DO NOT CLICK|
<br>
<br>
<b>!!!WAIT!!</b> Before you do anything else it shows that the alert was alerting to a <b>Phishing URL Detected</b>. Now this takes us to step 3.<br><br>

<b>STEP 3</b><br>
Here is a link that provides 3rd party tools to help Analyze the suspicious URL:<br>

<a href="https://app.any.run/">AnyRun</a><br>
<a href="https://www.virustotal.com/gui/home/upload">VirusTotal</a><br>
<a href="https://urlhaus.abuse.ch/verify-ua/">URLHouse</a><br>
<a href="https://urlscan.io/">URLScan</a><br>
<a href="https://www.hybrid-analysis.com/">HybridAnalysis</a><br>
<br>
For this alert, I will be using both <b>VirusTotal</b> and <b>AnyRun</b>. After inserting the link to both tools, it is shown that this link is coming back to several <b>phishing</b> and <b>malware</b> alerts. Now that we have confirmed this link is a threat we can head to step 4.<br><br>

<b>STEP 4</b><br>
It is important to find out if anyone has accessed the URL domain within the organization. We can view this activity by heading to the <b>"LOG MANAGEMENT"</b> to obtain this information. While investigating keep the following questions in mind: <br><br>
When was it accessed?<br>
What is the source address?<br>
What is the destination address?<br>
Which user tried to access?<br>
What is User Agent?<br>
Is the request blocked?<br>

Based on the information provided, all links were coming from the client hostname EmilyComp with an IP address of <b>172.16.17.49</b> on a Windows operating system. After viewing the browsing history, this also shows several links that I have thrown into VirusTotal with a result of phishing and malware detection. Now that we know where the device is coming from it is safe to say that we need to <b>"CONTAIN"</b> this device from receiving future threats which could harm the organization/network.<br><br>

<b>STEP 5</b><br>
It is now time to wrap up the alert after confirming this as a <b>TRUE POSITIVE</b> alert. Start by attaching your documents/findings to the artifacts provided on Let's Defend. <br><br>

<b>SUMMARY:</b> After thoroughly investigating the alert, I discovered that the user, identified as "Ellie" under the account "EmilyComp," had accessed several suspicious links. To ensure a comprehensive analysis, I conducted due diligence by inputting the provided links into third-party URL detection tools. These tools confirmed that each link was associated with malicious activity, specifically categorizing them as either malware or phishing URLs. As a result of this confirmation, I took immediate action to contain the affected device and prevent any further security threats. I then escalated the alert, classifying it as a true positive, meaning that it was a legitimate security threat.

