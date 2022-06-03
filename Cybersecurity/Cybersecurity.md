# Cybersecurity

### Acronyms
| Acronym | Description |  
| --- | --- | 
| 2FA | Two-Factor Authentication |  
| BaaS | Backup as a Service |  
| FIDO | Fast Identification Online |  
| EK | Exploit Kit |  
| FAQs | Frequently Asked Questions |  
| MFA | Multi Factor Authentication | 
| MTAC | Multiple Threat Alert Center |  
| PaaS | Platform as a Service | 
| SaaS | Software as a Service |  
| USF | Universal Second Factor |  

### Links
- [Articles by @thegrugq](https://medium.com/@thegrugq)
  - [Travel Security Advice](https://medium.com/@thegrugq/stop-fabricating-travel-security-advice-35259bf0e869)}
- [Articles by Bleeping Computer](https://www.bleepingcomputer.com/news/security/)
  - [USB is scary](https://www.bleepingcomputer.com/news/security/heres-a-list-of-29-different-types-of-usb-attacks/)
- [Articles by TechSolidarity](https://techsolidarity.org/)
  - [Do's and Don'ts for journalists](https://techsolidarity.org/resources/basic_security.htm)
- [FIDO Alliance](https://fidoalliance.org/)
- [RoboKiller](https://robokiller.com/)
  -  Lookup Phone Numbers on RoboKiller
    ```url
    https://lookup.robokiller.com/p/272-227-2235
    ```
- [Roll Your Own Crypto](https://www.schneier.com/blog/archives/2015/05/amateurs_produc.html)
- [Scan a Download Link for Malware](https://www.virustotal.com/#/home/upload)  
- [USB data blocker](https://www.amazon.com/dp/B00QRRZ2QM/)
- [YubiKey](https://www.yubico.com/)

**MIT Training**
  - [Computer Systems Security (https://css.csail.mit.edu/6.858/)
  - [Cryptography 1](https://courses.csail.mit.edu/6.857/)
  - [Cryptography 2](https://courses.csail.mit.edu/6.875/)

**Password Managers**
 - [1password](https://1password.com/)
 - [KeePass](https://keepass.info/)
 - [BitWarden](https://bitwarden.com/)
 - [`pass`](https://www.passwordstore.org/)
 - 
**US Governament**
  -	[Department of Homeland Security (DoHS)](https://www.dhs.gov/national-cyber-security-awareness)
  -	[Navy's CyberSecurity](https://www.navy.mil/local/cyberawareness/)
  - [US CERT](https://www.us-cert.gov/)

### Procedures

#### Disable Google Assitant on Android

To turn off “Hey Google” or to stop “OK Google,” follow these steps:

  1. Navigate to Settings Select
  2. Google > Account Services > Search, Assistant & Voice > Voice
  3. Select Voice Match and, finally, toggle off “Hey Google” 

Delete your voice request history on Google Assistant to ensure that this no memory bank of your conversation and to ensure your potentially sensitive information is not at risk in the event of a cyberattack.

#### Disable microphone access across applications

In addition to turning off virtual assistant apps like Siri and “Hey Google,” you might want to stop other applications like social media platforms from accessing your microphone, too.

- To disable microphone access on iOS devices, navigate to Settings > [a specific application] > Settings, and then toggle off Microphone.
- To disable microphone access on Android devices, navigate to Settings > Applications > Applications Manager > [a specific application] > Permissions, and then select “Turn Off the mic.” 

#### Terminology 
| Terminology | Description | Source |
| --- | --- | --- |  
| Botnet | a collection of internet-connected devices which may include computers (private or public), servers, mobile devices, or internet of things (IoT; refrigerators, alarms systems, media players) infected with malicious software and controlled as a group without the owner’s knowledge to perform cyberattacks or various scams. | IT, Malware |  
| Exploit Kits | Exploit kits (EKs) are computer programs designed to find flaws, weaknesses or mistakes in software apps and use them to gain access into a system or a network. |  
| Misconfiguration | Simply failing to validate your security or privacy settings in apps such as video conferencing could potentially expose your chats to eavesdroppers. |  
| Password Sniffing | This is a tactic used by cyber criminals to harvest passwords. They do this through monitoring and snooping in on network traffic to retrieve password data. |  
| Phishing | used to steal sensitive information (credit card data, usernames, and passwords, etc.) from users. The attackers pretend to be a trustworthy entity (usually by copying the look and feel of a big brand) to trick the victims into revealing their confidential data; a technique for attempting to acquire sensitive data, such as bank account numbers, SSN, date of birth, etc. through a fraudulent solicitation in e-mail, SMS text, or on a web site, in which the perpetrator masquerades as a legitimate business or reputable person. | IT, Malware |  
| Vulnerabilities | Humans are fallible, and so is their code. Check your devices to ensure they are up to date with their security patches and/or firmware from trusted sources. |  
| Zero Trust | a foundational security tenet that no actor, system, network or service operating outside or within the security perimeter should be trusted automatically |  

These are just a few of the many attacks that can be used to capture your data.  So remember to encrypt, use complex passwords, use Multi Factor Authentication (MFA) when available and be vigilant.  Know what your clicking on or responding to and don't give your information out.

## Access Security
Two Factor Authentication (2FA) adds an extra layer of protection to your accounts on top of passwords. In order to login, you not only have to know some password, but you also have to "prove" in some way you have access to some hardware device. In the most simple case, this can be achieved by receiving an SMS on your phone, although there are [known issues](https://www.kaspersky.com/blog/2fa-practical-guide/24219/) with SMS 2FA. A better alternative we endorse is to use a [U2F](https://en.wikipedia.org/wiki/Universal_2nd_Factor) solution like [YubiKey](https://www.yubico.com/).

### Two-Factor Authentication  
- [Google](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=2&ved=0CH0QFjAB&url=https%3A%2F%2Fsupport.google.com%2Faccounts%2Fbin%2Fanswer.py%3Fhl%3Den%26answer%3D180744&ei=FMbgT5XqEenE2gXvl7XsCw&usg=AFQjCNENeGTuD_cqnq0Bx6WZWKVgjugB1g) has two-factor authentication both for SMS and with a handy mobile app—read [our guide to installing and configuring the mobile app here](https://www.howtogeek.com/105041/how-to-secure-your-google-account-with-google-authenticator/).  
- LastPass offers [multiple forms of multi-factor authentication](http://helpdesk.lastpass.com/security-options/#Multifactor+Authentication+Options) including [using Google Authenticator](http://helpdesk.lastpass.com/security-options/google-authenticator/). We have a guide to [configuring it](https://www.howtogeek.com/104666/how-to-make-lastpass-even-more-secure-with-google-authenticator/).  
- Facebook has a two-factor system called [login approvals](http://www.facebook.com/note.php?note_id=10150172618258920) that uses SMS to confirm your identity.
  
### SSO: Single Sign On
- [Angular SSO example](https://github.com/jlguenego/angular-sso-example) 
- [React SSO example](https://github.com/jlguenego/react-sso-example) 
- [Vue SSO example](https://github.com/jlguenego/vue-sso-example) 

## Cloud Security!

#### What is the cloud?
Cloud computing is essentially the offering of an application or service that is offered over numerous devices, or locations. This can be provided over three different types of Cloud Computing. They are Private, Hybrid, and Public Cloud. Private would be based solely on the vendor's facility, while Hybrid would augment this location with some public facilities. Public Cloud would be provided totally on the outside by a vendor like the service provided by Amazon, or Microsoft.  Cloud computing is being used in our everyday life, such as banking, Email, media streaming, and Ecommerce (Amazon).

#### Here are some of the most popular Cloud Service types with examples:
- SaaS – Software as a Service – Office 365, Adobe, Facebook
- PaaS – Platform as a Service – Amazon, Online Games, Apple, Google Drive
- BaaS – Backup as a Service – Amazon, Microsoft products, Apple

#### What risks are there for cloud use at home?
Cloud computing brought home users a way to use their data across multiple devices and made it available on the go.  The inherent problems that exist for that level of availability are many.  You may not think your data is at that great of risk, but you must remember, that someone is always looking to get easy score of data and use it maliciously.   Here are some of the types of attacks that actors use:

## Communicatrion Security

### Identify eMail Scams

Indicators that an email, text message, or website is fake:  
1.	When hovering a mouse over a link, the destination web address does not match the web address a user intends to visit.
2.	An email, text message, website, or phone call has an unusual or urgent request for information.
3.	The images are blurry, altered, or slightly different colors than the legitimate versions.
4.	Misspelled words, grammar issues, or a slight change in the language used, compared to the legitimate version of the website.
5.	The web page or email does not display important company information, such as company contact information.
6.	A deal that seems too good to be true
**Source**: NCIS Multiple Threat Alert Center (MTAC)

### Phone & Tablet App Precautions

Below are precautions that personnel can take to help safeguard sensitive information while using a mobile device:
- Read the "terms and conditions" associated with each app
- Research the background information of apps and companies who develop them
- Only download apps from trusted sources
- Only allow permissions that are necessary for each app.  For example, a photo editing app should not require access to a user's GPS location
- Only download apps that are necessary and delete apps that are no longer needed
- Limit the amount of personal and financial data that is stored on apps
- Read app reviews prior to downloading
- Use different username and password combinations for different online services and apps, and change the passwords often
**Source**:  NCIS Multiple Threat Alert Center (MTAC)

## Phishing

### Recent FBI Email Scam
Please review the following user communications concerning "phishing" and other email scams that have been reported: 
-	User Awareness of "Phishing" at http://homeport/alerts/status_alert_display.asp?comno=20050111-0925 
-	Navy Federal Credit Union Phishing Scam at http://homeport/alerts/status_alert_display.asp?comno=20050610-1130 

Other email scams exist in today's environment, so users are reminded to remain vigilant concerning Internet and email security. Opening emails from unknown persons, or emails that contain links pointing to unexpected locations may allow malicious code to enter the NMCI Enterprise from unidentified virus threats.  
Users receiving emails of this specific nature are encouraged to report it to the Internet Crime Complaint Center at https://www.ic3.gov.  

## Prevent Cryptocurrency Mining
Install the No Coin extension, available for Google Chrome, Mozilla Firefox, and Opera. It’s open source, is the most popular extension of its type, and does a great job of blocking Coin Hive and other similar cryptocurrency miners.  

## Make the Internet Safer and More Secure 
Followthese simple tips:
-	**Enable stronger authentication on Websites**.  Always enable stronger authentication for an extra layer of security beyond the password that is available on most major email, social media and financial accounts.  Stronger authentication (e.g., multi-factor authentication that can use a one-time code texted to a mobile device) helps verify that a user has authorized access to an online account.   
-	**Make your passwords long & strong** when you use passwords. Use complex passwords with a combination of numbers, symbols, and letters.  Use unique passwords for different accounts.  
-	**When in doubt, throw it out**.  Links in email and online posts are often the way cyber criminals compromise your computer.  If it looks suspicious (even if you know the source), delete it.  
-	**Share with care**.  Limit the amount of personal information you share online and use privacy settings to avoid sharing information widely.  
-	**Keep a clean machine**.  Update the security software, operating system, and web browser on all of your Internet-connected devices.  Keeping your security software up to date will prevent attackers from taking advantage of known vulnerabilities.  
-	**Back it up**.  Make electronic and physical back-ups or copies of all your important work.  Data can be lost in many ways including computer malfunctions, malware, theft, viruses, and accidental deletion.  

## Spyware & Adware
1.	When visiting web sites, do not click on the pop up ads that appear. Often Spyware will install once a user clicks on a link within a pop up window. Close all pop up windows by clicking on the "X" in the top right hand corner of the pop up window. 
2.	Be sure to read and completely understand any "User Agreements" that appear on web sites before responding "I Agree". 
3.	To exit unfamiliar web sites you may have been redirected to, click on the "X" in the upper right hand corner to close the browser window. Users are strongly encouraged not to click anywhere within the browser window, as this may result in unintentional installation of Spyware on your NMCI workstation.

