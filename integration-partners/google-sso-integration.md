---
description: Use steps below to configure Google SSO Integration with CircleHD Portal
---

# Google SSO Integration

1. First, login to your CircleHD portal with your admin credentials, and navigate to Portal Settings =&gt; Single Sign On \(SSO\), which should be at https://&lt;YOUR DOMAIN&gt;.circlehd.com/admin/sso 

![CircleHD Portal - SSO Settings](../.gitbook/assets/image%20%2827%29.png)

2. Turn On Enable Single Sign On Switch if its not already turned on. It should display SAML SSO Url, Metadata Uri and Test URL. Copy "Single Signon URL" and keep it handy for future steps.

3. Go to Google Admin ****[https://admin.google.com/](https://admin.google.com/) , you will need to use your admin login and your Google account should be a GSuite account. 

![Google Admin Account - Apps](../.gitbook/assets/image%20%287%29.png)

4. Click on "SAML apps", then Click on "+" sign at bottom right, that says "Enable SSO for a SAML Application".

![Step 1 - Enable SSO in Google](../.gitbook/assets/image%20%2829%29.png)

4. There will be a popup Step 1, Click the link "Setup my own custom App" link below on the popup. It will load IDP information Dialog box, which is Step 2.

![Step 2 - Enable SSO in Google](../.gitbook/assets/image%20%2826%29.png)

5. Click on Download near certificate. Keep the certificate file handy.

6. Copy the SSO Url and keep it handy for steps required in CircleHD portal.

7. Click on Next, it will load another box to enter application information. Enter Application Name as "CircleHD".

![Step 3 - Enable SSO in Google](../.gitbook/assets/image%20%2824%29.png)

8. For CircleHD logo, you can download from [https://www.circlehd.com/docs/presskit.html](https://www.circlehd.com/docs/presskit.html). You can upload "icon-1024x1024.png" to "Upload Logo" option in Google SSO Steps. Click Next 

 9. For Step 4 of Google SSO, you will need to enter ACS URL and related information. ACS URL can be copied from the CircleHD SSO settings page \(shown in \#1 above\). Entity Id will be same as ACS URL. Start URL will be your Enterprise CircleHD platform URL. Select Signed Response. 



![Step 4 - Enable SSO in Google](../.gitbook/assets/image%20%2832%29.png)

10. For Name ID, select Basic Information, Primary Email. 

11. For Name ID Format, select Email. Click Next

12. Step 5 of Google SSO Setup, will be attribute mapping. Add display\_name, Basic Information and First Name. Click Finish. This would complete the setup on Google SSO side. Feel free to add more attributes as needed here which will be sent along with the SSO login.

![Step 5 - Enable SSO in Google](../.gitbook/assets/image%20%2818%29.png)

13. Go to downloaded certificate file done in \#5, open it in code editor such as notepad++, Visual Studio, etc. Copy the certificate. Please do not open in regular Notepad App.

14. Go back to CircleHD SSO Settings page, same as \#1. Paste the certificate under the "Certificate" text box.

15. Login URL will be the ACS URL from \#9 above.

16. Logout URL can be left blank for now.

17. Click "Save". Follow Steps below to test the SSO integration.

## Test the Integration

1. Navigate to the Sign in Test URL : https://&lt;YOUR DOMAIN&gt;.circlehd.com/auth/saml2/signin
2. Make sure you are able to login to CircleHD domain using your Org SSO Credentials.
3. Test this integration from a different browser or Incognito mode.
4. Make sure new users can log-in from the test URL without having to be invited first.
5. If any of the test fail, you can try again by repeating above steps. If issue persists, please reach out to CircleHD Support at support@circlehd.com.

## Activate SSO Throughout The Site

When above Steps and Tests are successful, you have dual authentication mode turned on. Your users will automatically be provisioned when logging in via SSO. However when they access URL directly they will be prompted to enter password.

To activate SSO throughout the site: Please Contact CircleHD support at support@circlehd.com

## Help & Support

If you need help anytime during the process you can send a request via [https://www.circlehd.com/contactus/](https://www.circlehd.com/contactus/) or contact CircleHD support at support@circlehd.com

