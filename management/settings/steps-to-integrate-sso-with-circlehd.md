# Steps to Integrate SSO with CircleHD

**1-** First, login to your CircleHD portal with your admin credentials, and navigate to Portal Settings -&gt; Single Sign On \(SAML\), which should be at https://&lt;YOUR DOMAIN&gt;.circlehd.com/admin/sso 

**2-** Turn On Enable Single Sign On Switch **\[1\]**.

![](../../.gitbook/assets/sso%20%282%29.png)

**3-** Provide the Metadata/Audience XML **\[2\]** \(https://&lt;YOUR DOMAIN&gt;.circlehd.com/auth/saml2/metadata.xml\) to your IT SSO Admin. The document contains information about Audience system that allows your instance to verify that it is the intended recipient of a SAML response and generate corresponding certificate to be used by CircleHD. 

**4-** Additionally, your Organization IT SSO Admin may ask for the following information and / or configurations,

<table>
  <thead>
    <tr>
      <th style="text-align:left">1</th>
      <th style="text-align:left">App name</th>
      <th style="text-align:left">CircleHD</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">2</td>
      <td style="text-align:left">App logo</td>
      <td style="text-align:left">DOWNLOAD FROM <a href="https://static.circlehd.com/img/circlehd-presskit.zip">https://static.circlehd.com/img/circlehd-presskit.zip</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">3</td>
      <td style="text-align:left">Single sign on URL</td>
      <td style="text-align:left">https://&lt;YOUR DOMAIN&gt;.circlehd.com/auth/saml2</td>
    </tr>
    <tr>
      <td style="text-align:left">4</td>
      <td style="text-align:left">Use this for Recipient URL and Destination URL</td>
      <td style="text-align:left">Yes</td>
    </tr>
    <tr>
      <td style="text-align:left">5</td>
      <td style="text-align:left">Audience URI (SP Entity ID)</td>
      <td style="text-align:left">https://&lt;YOUR DOMAIN&gt;.circlehd.com/</td>
    </tr>
    <tr>
      <td style="text-align:left">6</td>
      <td style="text-align:left">Default RelayState</td>
      <td style="text-align:left">Empty</td>
    </tr>
    <tr>
      <td style="text-align:left">7</td>
      <td style="text-align:left">Name ID format</td>
      <td style="text-align:left">EmailAddress</td>
    </tr>
    <tr>
      <td style="text-align:left">8</td>
      <td style="text-align:left">Application Username</td>
      <td style="text-align:left">Email</td>
    </tr>
    <tr>
      <td style="text-align:left">9</td>
      <td style="text-align:left">Response</td>
      <td style="text-align:left">Signed</td>
    </tr>
    <tr>
      <td style="text-align:left">10</td>
      <td style="text-align:left">Assertion Signature</td>
      <td style="text-align:left">Signed</td>
    </tr>
    <tr>
      <td style="text-align:left">11</td>
      <td style="text-align:left">Signature Algorithm</td>
      <td style="text-align:left">RSA-SHA256</td>
    </tr>
    <tr>
      <td style="text-align:left">12</td>
      <td style="text-align:left">Digest Algorithm</td>
      <td style="text-align:left">SHA256</td>
    </tr>
    <tr>
      <td style="text-align:left">13</td>
      <td style="text-align:left">Assertion Encryption</td>
      <td style="text-align:left">Unencrypted</td>
    </tr>
    <tr>
      <td style="text-align:left">14</td>
      <td style="text-align:left">Optional SAML Attributes (used for reporting)</td>
      <td style="text-align:left">
        <p>fname: <em>&quot;&lt;FIRST NAME&gt;&quot;</em>
        </p>
        <p>lname: <em>&quot;&lt;LAST NAME&gt;&quot;</em>
        </p>
        <p>display_name: <em>&quot;&lt;DISPLAY NAME&gt;&quot;</em>
        </p>
        <p>department: <em>&quot;&lt;ORG/DEPARTMENT&gt;&quot;</em>
        </p>
        <p>function_name: <em>&quot;&lt;JOB FUNCTION&gt;&quot;</em>
        </p>
        <p>manager: <em>&quot;&lt;MANAGER EMAIL&gt;&quot;</em>
        </p>
        <p>cost_center: <em>&quot;&lt;COST CENTER&gt;&quot;</em>
        </p>
        <p>rtd_chain: <em>&quot;&lt;REPORTING CHAIN (separated by comma)&gt;&quot;</em>
        </p>
        <p>location: <em>&quot;&lt;LOCATION&gt;&quot;</em>
        </p>
      </td>
    </tr>
  </tbody>
</table>

**5-** Receive the following information from your IT SSO Admin to continue. This may be contained in the Identity Provider metadata XML File

* **Login URL \[4\]** \(Identity Provider Single Sign-On URL\) :  TO BE USED FOR REDIRECTING USER WHEN AUTHENTICATION IS REQUIRED.
* **Logout URL \[5\]:** \(OPTIONAL\) THE DESTINATION FOR THE USER WHEN LOGGING OUT FROM CIRCLEHD.
* **Certificate \[6\]:** X509 PUBLIC KEY CERTIFICATE TO VALIDATE THE RESPONSE FROM YOUR IDP. 
* Fill in all the Fields accordingly.

**6-** Click on the "**Save**" button **\[7\]** to save SSO Settings.

## Test the Integration

**1-** Navigate to on the Sign in Test URL **\[3\]**: https://&lt;YOUR DOMAIN&gt;.circlehd.com/auth/saml2/signin

**2-** Make sure you are able to login to CircleHD domain using your Org SSO Credentials.

**3-** Test this integration from a different browser or Incognito mode.

**4-** Make sure new users can log-in from the test URL without having to be invited first.

**5-** If any of the test fail, you can try again by repeating above steps. If issue persists, please reach out to CircleHD Support at support@circlehd.com.

## Activate SSO Throughout The Site

When above Steps and Tests are successful, you have dual authentication mode turned on. Your users will automatically be provisioned when logging in via SSO. However when they access URL directly they will be prompted to enter password.

To activate SSO throughout the site: Please Contact CircleHD support at support@circlehd.com

## Help & Support

If you need help anytime during the process you can send a request via [https://www.circlehd.com/contactus/](https://www.circlehd.com/contactus/) or contact CircleHD support at support@circlehd.com

