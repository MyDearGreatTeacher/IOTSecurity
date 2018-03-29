# IoT Attack Surface Areas 物聯網攻擊面向

 Attack Surface	Vulnerability

## Ecosystem Access Control	

Implicit trust between components

Enrollment security

Decommissioning system

Lost access procedures

## Device Memory攻擊設備的記憶體	

Cleartext usernames

Cleartext passwords

Third-party credentials

Encryption keys

##  Device Physical Interfaces	攻擊設備的實體存取介面

Firmware extraction提取韌體

User CLI

Admin CLI

Privilege escalation

Reset to insecure state

Removal of storage media

Device Web Interface	

SQL injection

Cross-site scripting

Cross-site Request Forgery

Username enumeration

Weak passwords

Account lockout

Known default credentials

Device Firmware	

Hardcoded credentials

Sensitive information disclosure

Sensitive URL disclosure

Encryption keys

Firmware version display and/or last update date

Device Network Services	

Information disclosure

User CLI

Administrative CLI

Injection

Denial of Service

Unencrypted Services

Poorly implemented encryption

Test/Development Services

Buffer Overflow

UPnP

Vulnerable UDP Services

DoS

Administrative Interface	

SQL injection

Cross-site scripting

Cross-site Request Forgery

Username enumeration

Weak passwords

Account lockout

Known default credentials

Security/encryption options

Logging options

Two-factor authentication

Inability to wipe device

Local Data Storage	

Unencrypted data

Data encrypted with discovered keys

Lack of data integrity checks

Cloud Web Interface	

SQL injection

Cross-site scripting

Cross-site Request Forgery

Username enumeration

Weak passwords

Account lockout

Known default credentials

Transport encryption

Insecure password recovery mechanism

Two-factor authentication

Third-party Backend APIs	

Unencrypted PII sent

Encrypted PII sent

Device information leaked

Location leaked


Update Mechanism	


Update sent without encryption



Updates not signed



Update location writable



Update verification



Malicious update



Missing update mechanism



No manual update mechanism



Mobile Application	


Implicitly trusted by device or cloud



Username enumeration



Account lockout



Known default credentials



Weak passwords



Insecure data storage



Transport encryption



Insecure password recovery mechanism



Two-factor authentication


Vendor Backend APIs	



Inherent trust of cloud or mobile application



Weak authentication



Weak access controls


Injection attacks



Ecosystem Communication	



Health checks


Heartbeats



Ecosystem commands



Deprovisioning



Pushing updates



Network Traffic	


LAN



LAN to Internet



Short range



Non-standard



