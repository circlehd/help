---
description: >-
  Follow the industry standard best practices to keep your secure integration of
  your IDP and CircleHD compliant
---

# SSO Key Rotation

At CircleHD we treat security as our main feature. Right from user authentication to backup data handling we have followed the industry standard best practices to keep your data secure.

### Why key rotation is necessary?

CircleHD Simplified user authentication or Single Sign On \(SSO\) is made secure by trust established over RSA 2048 bit public key infrastructure. That requires both parties \(IDP: Your Side and SSP: CircleHD\) to sign and verify challenges and responses with an established cryptographic key. If the keys were compromised due to any reason the trust is broken. Therefore key rotation is a best practice to keep the trust established.

### When to update the keys?

We rotate our keys twice a year and there is no significant impact or downtime at your end. Your IDP may rotate keys periodically. Typically once or more every year. Please refer to your IT administrator to plan for certificate rotation and downtime. Although SSO continue to work with out any rotation, we recommend rotating keys at-least once every year.

### Key rotation at your end IDP

When your IDP rotates keys you must update CircleHD SSO configuration. If key expires at your end, Single Sign On Authentication will fail.

#### Prerequisite

Only admins on CircleHD can rotate keys. If you don't have admin permission, please contact your admin or support@circlehd.com for additional help.

1. New Certificate File.
2. Two browser sessions \(Optional, but recommended\)
3. Plain Text Editor such as Notepad or Sublime Text

#### **Open 2 browser sessions.**

To update the SSO, navigate to **Portal Settings** -&gt; **Single Sign On**

{% hint style="info" %}
It is highly recommended to open a different browser window to perform the Certificate rotation. If you don't have another browser installed try using the Chrome Incognito mode or Safari Private window.
{% endhint %}

Backup the current certificate by Copying into a text editor such as Notepad or Sublime Text and save the file to disk.

Open the key provided by your IT admin using a text editor. Paste the certificate content into the Certificate box \#3 below.

Click Save.

Log out and Log In back to make sure your changes have taken effect. **If everything works, we are done.**

### If update fails:

If there is an issue with the SSO. Go back to the previous browser session and replace the certificate. Click Save.

Navigate to yoursite.circlehd.com in a different browser window to make sure you can login using the old certificate.

Contact CircleHD. Email support@circlehd.com

![](../.gitbook/assets/sso%20%281%29.png)

