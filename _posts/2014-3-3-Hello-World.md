---
layout: post
title: CVE-2019-12863
published: true
---
##  Stored HTML Injection vulnerability in SolarWinds Orion Platform "CVE-2019-12863"

**Discoverer: Shashank Chaurasia**

**INTRODUCTION**

SolarWinds® Network Performance Monitor (NPM) is a powerful and affordable network monitoring software that enables you to quickly detect, diagnose, and resolve network performance problems and outages. NPM is a Multi-vendor network monitoring that scales and expands with the needs of your network, Key Features includes  Multi-vendor network monitoring, Network Insights for deeper visibility, Intelligent maps, NetPath and PerfStack for easy troubleshooting, Smarter scalability for large environments and Advanced alerting.

### Security Researcher – Shashank Chaurasia found a Stored HTML Injection vulnerability in the SolarWinds Orion Platform 2018.4 HF3 (NPM 12.4, NetPath 1.1.4) and it has been assigned CVE-2019-12863 by the MITRE.


**Description**: HTML injection is a type of injection issue that occurs when a user is able to control an input point and is able to inject arbitrary HTML code into a vulnerable web page. This vulnerability can have many consequences, like disclosure of a user’s session cookies that could be used to impersonate the victim, or, more generally, it can allow the attacker to modify the page content seen by the victims.

This vulnerability occurs when the user input is not correctly sanitized and the output is not encoded. An injection allows the attacker to send a malicious HTML page to a victim. The targeted browser will not be able to distinguish (trust) the legit from the malicious parts and consequently will parse and execute all as legit in the victim context.

**Platform/Product**: SolarWinds Orion Platform 2018.4 HF3 (NPM 12.4, NetPath 1.1.4)

**Vulnerability Name**: Stored HTML Injection by administrators via the Web Console Settings screen

**Affected Component**: Solarwinds-Orion-NPM.exe

**Attack Type**: Local

**Impact**

A possible attack scenario is demonstrated below:

Attacker discovers injection vulnerability and decides to use an HTML injection attack
Attacker crafts malicious link, including his injected HTML content, and sends it to a user via email
The user visits the page due to the page being located within a trusted domain
The attacker’s injected HTML is rendered and presented to the user asking for a username and password
The user enters a username and password, which are both sent to the attackers server

User is able to control an input point and is able to inject arbitrary HTML code into a vulnerable web page. This vulnerability can have many consequences, like attacker can re-direct the victim to malicious site, or, more generally, it can allow the attacker to modify the page content seen by the victims.

**Recommendation**
The preferred option is to properly escape all un-trusted data based on the HTML context. Include data escaping techniques in their applications.
Use positive or “white-list” input validation to protect against XSS.
Use HTML & URL encoding for applications which accept special characters and meta tags. Such validation should decode any encoded input, and then validate the length, characters, and format on that data before accepting the input.
Client side and server side validation should be implemented. Server side validation is mandatory
Method of Exploitation

**Steps to Reproduce** :-

1) Download the trial software exe file from https://www.solarwinds.com/network-performance-monitor.

2) Install the exe file.

3) Open orion web console (hostname of system:8787)
![]({{site.baseurl}}/https://github.com/ShashankChaurasia/ShashankChaurasia.github.io/blob/08baaf205f76dac19be23177951efca5f8e63668/Assets/Images/1.png)

4) Enter admin as username and “blank” as password.
![2.png]({{site.baseurl}}/_posts/2.png)

 5) Go to settings > all settings
 ![3.png]({{site.baseurl}}/_posts/3.png)

6) Then go to Product specific settings >Web console settings
![4.png]({{site.baseurl}}/_posts/4.png)

 7) here you can see Site login text box.
![5.png]({{site.baseurl}}/_posts/5.png)

 8) Here enter your malicious html for example “<h1><a href=”http://www.evilwebsite.com“>Click Here for Login</a></h1>”  <h1><a href=”http://www.evilwebsite.com”>ShashanK</a></h1>
 ![6.png]({{site.baseurl}}/_posts/6.png)

 9) now submit the changes and logout of the application.
 ![7.png]({{site.baseurl}}/_posts/7.png)

10) Now on the login page you can see the modified content. Upon hovering we can see it will redirect to http://www.evilwebsite.com. This is Stored HTML Injection.
![8.png]({{site.baseurl}}/_posts/8.png)

**Disclosure Process**:

Reported the Vulnerability to the Vendor Security or PSIRT Team
Acknowledged confirmed from the Vendor that vulnerability exist
CVE has been filed in NVD
Vendor confirm that the vulnerability is fixed or a latest version, patch is released
Vulnerability disclosed to the public
 

**Reference**: https://www.solarwinds.com/network-performance-monitor  


[Has vendor confirmed or acknowledged the vulnerability?]

Yes
