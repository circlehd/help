# How to secure Video / Media access using SSO Access Control List \(ACL\)?

For Portals using SSO SAML logins, Video / Media access can be secured by using SSO ACL \(Access Control Lists\). For each user that logs in using SSO, the ACL attributes will need to be sent by the SSO provider. You can follow below steps to secure a video using ACL.

1. Click on the Video to go to Video detail page, click on "Edit" Video to view Video properties. 

![Video Detail Page - Edit button](../.gitbook/assets/image%20%2812%29.png)

2. This will load the Video properties page shown below. Scroll all the way down until you see SSO Access Control List label. This will display a text box to enter criteria for SSO Access Control List as shown below. 

![Video Edit Page - SSO ACL Access](../.gitbook/assets/image%20%289%29.png)

3. The format for entering SSO ACL condition is $&lt;attribute name&gt; = &lt;value&gt;. For e.g. $costcenter=34, $organization=product marketing, $department=Finance, etc.

4. Once you enter the condition in the SSO text box, click on Save. Please make sure there is no typo in the attribute name and value as it has to match the exact values and case that SSO provider sends with the user. 

5. Once this is saved, it should restrict video / media access as per the condition entered in SSO text box.

6. Please make sure all required attributes are passed through SSO login, your IT team will be able to help confirm this. 

If any questions or further help needed on this, please email support@circlehd.com

