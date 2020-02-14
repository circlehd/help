# How to secure view access to a Channel using SSO Access Control List?

For Portals using SSO logins, Channels can be secured further by using ACL \(Access Control Lists\). For each user that logs in using SSO, the ACL attributes will need to be sent by the SSO provider. You can follow below steps to secure a channel using ACL.

1. Click on "Edit" Channel to view Channel properties. 

![Channel Details Page](../.gitbook/assets/image%20%2815%29.png)

2. This will load the Channel properties page shown below. Next to "Viewers" label, make sure you have disabled "Everyone" as shown in the picture. This will display a text box to enter criteria for SSO Access Control List. 

![Channel Edit Page](../.gitbook/assets/image%20%287%29.png)

3. The format for entering ACL condition is $&lt;attribute name&gt; = &lt;value&gt;. For e.g. $costcenter=34, $organization=product marketing

4. Once you enter the condition in the SSO text box, click on Save. Please make sure there is no typo in the attribute name and value as it has to match the exact values that SSO provider sends with the user. 

5. Once this is saved, it should restrict view access as per the condition entered in SSO text box.

6. Please make sure all required attributes are passed through SSO login. 



