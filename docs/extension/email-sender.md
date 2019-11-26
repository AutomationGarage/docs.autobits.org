---
title: Email Sender
sidebar_label: Email Sender
---

Lets you send emails.

It provides an *action* - `Send Email`.

Using this *action*, you can send emails from automation scenarios or as a reaction to an *event*.

The *action* has parameters:
 - `to` - email address of the recipient
 - `cc` - recipient of a carbon copy
 - `bcc` - recipient of a blind carbon copy
 - `subject` - subject of the email
 - `message` - email text *(Note: message should be in plain-text format)*

Emails can be sent to multiple addresses by using a comma to separate them:
```ini
to = jane.doe@example.com, somebody.else@example.com
```

The emails are sent via an external SMTP server, and AutoBits needs the following credentials to be able to connect to the server:
```ini
smtpServer = 
port = 
fromAddress = 
username = 
password = 
```
 - `smtpServer` - name or IP address of SMTP server
 - `port` - SMTP port
 - `fromAddress` - email address, that will be shown in 'From: ' field
 - `username` and `password` - are the credentials that are used to connect to the SMTP server.

##### Sending emails via Gmail
You can use public email providers(such as Gmail) to send emails. To send emails from a Gmail mailbox:

```ini
smtpServer = smtp.gmail.com
port = 587
fromAddress = [your Gmail email address]
username = [your Gmail email address]
password = [your Gmail password]
```
***Important Note:*** *Gmail does not allow apps to log-in with username & password by default. To permit username & password login for AutoBits: in your <a href="https://myaccount.google.com" title="Google Account Settings web page" target="_blank">Google account settings</a>, under "Sign-in & security" section, turn on a setting "Allow less secure apps"*

##### Sending emails via company mail server
Alternatively, if you run AutoBits inside a corporate network, most likely your organization already utilizes email server(SMTP server). Your company IT department can provide you with the credentials in that case.