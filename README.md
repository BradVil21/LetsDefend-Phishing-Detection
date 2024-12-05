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
  <b>Request UR:</b> http://mogagrocol.ru/wp-content/plugins/akismet/fv/index.php?email=ellie@letsdefend.io
  <br>
  <b>User Agent:</b> Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/79.0.3945.88 Safari/537.36
  <br>
  <b>Device Action:</b> Allowed
</div>
<br>
[Introduction: This repository showcases my work on implementing a phishing alert detection system using the Let's Defend platform. Let's Defend is an open-source Security Operations Center (SOC) platform for incident response and threat detection. In this project, I focused on detecting phishing alerts by integrating threat intelligence, analyzing suspicious emails, and leveraging automated detection mechanisms within Let's Defend. The primary goal was to identify phishing attempts in real-time by evaluating various indicators, such as: Suspicious URLs and domains, Email header anomalies, Malicious attachments or links, and Behavioral analysis of phishing attempts.]
<br>
<br>
Please also use this as a guide on how to work phishing alerts using Let's Defend. For any questions or concerns you can <b>CONTACT</b> me directly on <a href= "https://www.linkedin.com/in/bradley-vilsaint-414329267/">LinkedIn</a> or email <a href="info@letsdefend.io">info@letsdefend.io</a> for support.
<br>
<br>
<b>STEP1</b><br>
While working through this alert, it is important to keep track of what the alert has provided. <b>What should I do first?</b> Well good question. If you head to <b>"CASE PLAYBOOK"</b>, you are provided with details on what you should check for. Here is the collection data for this alert: <br><br>
*Source Address<br>
*Destination Address<br>
*User-Agent<br><br>

Based on the information already provided via the alert information you are already on the right track. <br><br>

*<b>Source Address:</b> 172.16.17.49<br>
*<b>Destination Address:</b>91.189.114.8<br>
*<b>User-Agent:</b>Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/79.0.3945.88 Safari/537.36<br><br>

<b>STEP2</b><br>
You will then search the logs for specific details within the <b>"LOG MANAGEMENT"</b> tab. 
