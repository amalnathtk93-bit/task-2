# **1. Introduction**



This report analyzes a suspicious email claiming to be from Payflow / PayPal Manager, received on 16 October 2025.

The investigation includes:



Header authentication (SPF, DKIM, DMARC, ARC)



Routing path analysis



Domain reputation checks



Social engineering and content review



Identification of Indicators of Compromise (IOCs)



Final verdict and recommendations



All personally identifiable information (PII) has been redacted.



# **2. Summary / Final Verdict**

🚨 THIS EMAIL IS A PHISHING / SCAM EMAIL.



Main reasons:



SPF Softfail → Unauthorized sending server



Mismatched recipient in header (receipt1@nydiscover.review)



Scam phone number requesting user to call



Fake account creation message



Suspicious domains (.review TLD)



Social engineering (fake $799.67 charge warning)



## **3. Email Header Analysis**



The raw header extracted from Gmail was analyzed using the Google Admin Toolbox — MessageHeader Analyzer.



##### **3.1 Header Summary (from your screenshot)**



(Screenshot attached in repo)



Field	Value

From	Payflow noreply@paypal.com



To	receipt1@nydiscover.review



Subject	Creation of your PayPal Manager user account

SPF	softfail – IP Unknown

DKIM	pass

ARC	pass

DMARC	pass

##### **3.2 SPF (Sender Policy Framework)**



Result: softfail — IP Unknown



This means the sending IP is not authorized to send emails for paypal.com.



✔ SPF failure = strong sign of spoofing

✔ Legitimate PayPal emails ALWAYS pass SPF



(Screenshot attached)



##### **3.3 DKIM (DomainKeys Identified Mail)**



Result: pass



But DKIM pass alone does NOT guarantee legitimacy because:



DKIM checks only header integrity



Scammers often abuse DKIM via forwarded messages



DKIM does NOT verify the content’s authenticity



Therefore DKIM pass does not clear this email.



##### **3.4 DMARC**



Result: pass



DMARC pass is misleading here because:



The ARC chain shows multiple hops



Forwarders can cause DMARC to pass



DMARC does NOT evaluate content safety



##### **3.5 ARC (Authenticated Received Chain)**



Result: pass



Pass simply means Gmail trusted the forwarding server.

It does not confirm that the original message was safe.



## **4. Routing Path Analysis**



Your routing timeline screenshot shows:



mx1.slc.paypal.com → Google  

mail-sor-f69.google.com → Google





However, the message took:



❌ 3+ minute suspicious delay

❌ forwarding through unknown sources

❌ SPF failed despite PayPal hops appearing



This proves the message did not cleanly originate from PayPal’s secure mail systems.



(Screenshot attached)



## **5. Domain \& Reputation Analysis**



A domain lookup was performed for manager.paypal.com.



✔ manager.paypal.com is legitimate.

❌ But your email did NOT come from that domain.

❌ The email was originally addressed to:



receipt1@nydiscover.review





The .review domain is:



Cheap



Commonly used in scam campaigns



Not associated with PayPal



## **6. Email Body / Content Analysis**



The content of the email (from your original message file) includes:



To Cancel payment of $799.67, contact PayPal at 1(805) 500-6956





This is a known scam technique called the “refund scam”:



✔ Scammer sends fake payment alert

✔ Victim panics

✔ Victim calls fake support number

✔ Scammer takes remote access or steals banking details



Additional Red Flags in Body:



Claims a PayPal Manager account was created



Asks you to “contact user to receive your password”



Lists fake account credentials:



Vendor : Paypaluser83272

User   : recepient669978





Tells you that you “just created a Payflow account”



PayPal NEVER:



Sends passwords



Creates accounts on your behalf



Uses random usernames



Sends alerts to unrelated domains



## **7. Social Engineering Indicators**

Attack Method	Evidence

Fear / Panic	“Payment of $799.67 created”

Urgency	“Call immediately to cancel”

Fake Support Number	1 (805) 500-6956

Credential Theft	Asks user to obtain password

Impersonation	Uses 'Payflow' and 'PayPal Manager' branding



This email uses classic refund-scam psychology.



## **8. Indicators of Compromise (IOCs)**

IOC Type	Value

Scam Phone Number	1 (805) 500-6956

Suspicious Domain	nydiscover.review

Suspicious Domain	padiscover.review

Spoofed Sender	noreply@paypal.com

Unauthorized Sending IP	(SPF softfail)

Fake Usernames	PayPalUser83272, recepient669978

Message ID	<05.0D.65421.20601F86@ccg13mail03>

## **9. Final Verdict**

🟥 This email is confirmed to be a PHISHING / REFUND SCAM email.



Despite DKIM/DMARC passes, the SPF softfail, recipient mismatch, scam phone number, suspicious domains, and fake account creation details confirm malicious intent.

