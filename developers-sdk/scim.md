---
description: This page is a guidance for how to enable SCIM integration with CircleHD
---

# SCIM

## Overview

SCIM \(System for Cross-Domain Identity Management\) is a federated provisioning protocol that provides a consistent API for user and group CRUD \(Create, Read, Update and Delete\) actions. With SCIM, administrators / developers can automate the exchange of user identity information between systems.

If your organization uses SAML SSO, you can implement SCIM to add, manage, and remove organization members' access to CircleHD.

If you use SAML SSO without implementing SCIM, you won't have automatic deprovisioning. When organization members' sessions expire after their access is removed from the IdP, they aren't automatically removed from the other systems. Authorized tokens grant access to the organization even after their sessions expire. To remove access, organization administrators / developers can either manually remove the authorized token from the organization or automate its removal with SCIM.

Below identity providers are compatible with CircleHD SCIM API.

* Azure AD
* Okta
* OneLogin

SCIM can also be used by administrators / developers to standardize the way user profile information is retrieved from a data source \(i.e. instead of having to manage connections to SQL tables, LDAP datastores and other data stores, SCIM provides a single interface to this data\).

### Model

SCIM 2.0 is built on an object model where a Resource is the common denominator and all SCIM objects are derived from it. It has id, externalId and meta as attribute and RFC7643 defines User, Group and EnterpriseUser that extends the common attributes. Read more at  [https://tools.ietf.org/html/rfc7643](https://tools.ietf.org/html/rfc7643)  

## SCIM Components and Roles

SCIM consists of three main components, as with a number of the federation protocols, the terminology could get slightly confusing so we describe the components below:

* _Service Provider_ Is the provider of the identity information \(in a traditional enterprise scenario, the SCIM Service Provider is most likely the same as the SAML Identity Provider\). For most of the examples in this guide, we will use Okta Directory as SCIM Service Provider. 
* _SCIM Consumer_ Is the application or service that will consume the SCIM data. For e.g., in a federated provisioning scenario, the SCIM Consumer is the 3rd party receiving the identity information, which is CircleHD in this scenario. 
* _Resource_ Is the object \(User / Group\) that SCIM request will be performed on.

## SCIM Actions

The SCIM protocol uses REST concept to define actions that a SCIM Consumer can perform on a resource managed by a SCIM Service Provider. Actions are mentioned below:  


<table>
  <thead>
    <tr>
      <th style="text-align:left">HTTP Verb</th>
      <th style="text-align:left">Action</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">GET</td>
      <td style="text-align:left">Reads resource (or resources) from Service Provider</td>
    </tr>
    <tr>
      <td style="text-align:left">POST</td>
      <td style="text-align:left">Creates new resource(s) at the Service Provider</td>
    </tr>
    <tr>
      <td style="text-align:left">PUT</td>
      <td style="text-align:left">Updates an existing resource, as this action requires the entire resource
        provided in the body, it would function more like a replace than an update</td>
    </tr>
    <tr>
      <td style="text-align:left">PATCH</td>
      <td style="text-align:left">
        <p>Updates existing resource with changes (wherever supported).</p>
        <p>Note: The PATCH action is optional and not supported in CircleHD currently</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">DELETE</td>
      <td style="text-align:left">Deletes resource at the Service Provider</td>
    </tr>
  </tbody>
</table>## SCIM Schema

SCIM provides a standard schema used to represent a user or a group. This schema is extensible so additional schema objects can be added or existing ones can be modified to provide custom schema support.

Along with the SCIM schema, specific data types are defined to simplify interoperability between integration partners.

### Accessing SCIM API

Similar to other CircleHD integration REST API's, the SCIM methods are accessed over the standby HTTP  protocol. Being a REST API, the HTTP verb \(e.g. GET or POST or PATCH or even DELETE\) used for each API method is critical. You will use GET to retrieve information, POST to create new objects, PUT and PATCH to modify objects, and DELETE to remove.  
  
The base URL for all calls to the SCIM API is https://&lt;subdomain&gt;.circlehd.com/api/scim/v2. All SCIM methods are extensions of this base URL.  


![CircleHD Cloud Identity Security Architecture](https://lh5.googleusercontent.com/X1W-SYHz3kaola9E-usJvcpMuB9Ma4M2iMaSEWcTut3fs5WpjRK4PlWnUwK0n2zZ7iWphxSyCWBtdxtJSP2-BppUpTP6P5BCHUrF-xNcYmJnoBM4O4cxQd9IZ9JZtQfO_fJvGF4)

### SCIM Endpoints

The SCIM API is RESTful and the endpoint URLs are not similar to other CircleHD API endpoints.

### How to enable SCIM for your organization?

The SCIM url can only be retrieved by an admin user in CircleHD. From the top right menu, navigate to Portal Settings, Select SCIM under Security Settings.  


![](https://lh4.googleusercontent.com/4zfsBOg7OgX0BGdw3dx34j4-DcA9M77zJP-tLbYFJc6jrC3VIHZR3q8BjWmp2Afvb5HdAD-qal6PR9DG5kYY7IjanavI9pSpRiYaQNjQm6lIRpQR-DwPRYlX8dR64C7ztN0IeJs)

Enable SCIM by turning the switch ON. Click save to generate the SCIM Password.  
  
NOTE: the password cannot be re-retrieved once this section is saved. You must note the password before proceeding.  
  
_Example_

<table>
  <thead>
    <tr>
      <th style="text-align:left">ENDPOINT</th>
      <th style="text-align:left">
        <p></p>
        <p>https://&lt;subdomain&gt;.circlehd.com/api/scim/v2
          <br />
        </p>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">USERNAME</td>
      <td style="text-align:left">scim</td>
    </tr>
    <tr>
      <td style="text-align:left">PASSWORD</td>
      <td style="text-align:left">generated above</td>
    </tr>
  </tbody>
</table>#### Authentication

SCIM Endpoint requires Basic Authentication. The username is SCIM.

### API

#### Service Provider Configuration

_GET /ServiceProviderConfigs_

Returns CircleHD's configuration details for our SCIM API, including which operations are supported.

#### 

#### Schemas

CircleHD currently supports schemas for users and groups. Querying the schemas will provide the most up-to-date rendering of the supported SCIM attributes.

_GET /Schemas/Users_

Returns CircleHD's configuration details for how users are formatted.

  
_GET /Schemas/Groups_

Returns CircleHD's configuration details for how groups are formatted, not supported currently in CircleHD.

#### 

#### Users

As you might expect, users map to the individuals of your team across a workspace or Grid organization. Each user contains properties called attributes, like userName and title. You can list users, filter by attribute, add new users, update a user's profile information, or remove a user entirely.

#### User Attributes

Attributes are the details associated with a user's account. These are the details that someone would typically set in their profile \(for example, by clicking the Edit Profile Button in the CircleHD web application\).  
  
The following tables map SCIM attributes to the profile fields that CircleHD uses. Most of these profile fields are exposed directly in a person's profile in the CircleHD UI.  
  
Sometimes, multiple SCIM attributes map to a single CircleHD profile field --- for example, CircleHD's Display name field will populate from either the displayName or the userName SCIM attribute, depending on which is set. If both are set, it will use displayName.  
  
Attribute values will vary by identity provider. For example, some may use a single field for a user's full name, others may provide sub-attributes such as givenName and familyName, still others may provide both. Either is acceptable, but they should only describe the same name \(i.e. sub-attributes should not contain additional or optional information, such as a nickname\).  
  
Not every attribute will be displayed in a user's profile --- for example, active does not appear as a field but can be used to determine if a user's account is active.  
  
The password attribute is never returned but can be used to set the initial password for a user if the team is not using an identity manager.  
  
_Standard attributes_

| Username | userName | string |
| :--- | :--- | :--- |
| Full Name | name, { givenName, familyName } | string |
| Nickname | nickName | string |
| Display Name | displayName, userName | string |
| Email | emails\[0\]\['value'\] | Array&lt;string&gt; |
| Profile URL | profileUrl | string |
| Profile Photo | photos\[0\]\['values'\] | Array&lt;string&gt; |

_Other Custom Attributes_

| CircleHD Field | SAML/SCIM Attribute | Data Type |
| :--- | :--- | :--- |
| EMPLOYEE NUMBER | employeeNumber | string |
| DEPARTMENT | department | string |
| JOB FUNCTION | function\_name | string |
| JOB\_TITLE | job\_title | string |
| MANAGER EMAIL | manager | string |
| COST CENTER | cost\_center | string |
| REPORTING CHAIN | rtd\_chain | Array&lt;string&gt; \(CSV\) |
| LOCATION | location | string |
| GROUP MEMBERSHIPS | groups | Array&lt;string&gt; \(CSV\) |

#### User Methods

_GET /Users_

Returns a paginated list of users, ten users per page by default. When querying large CircleHD instances, reduce the count parameter to 1000 or less, and use the startIndexparameter to paginate through users.  
  
It's possible to return a list of specific types of users with the filter parameter.  
  
`GET /api/scim/v2/Users?startIndex=4&count=500 HTTP/1.1  
Host: <your subdomain>.circlehd.com  
Accept: application/json  
Authorization: Basic nyzxSLInlhff5tOxuGpeC29iEe9c=`  
  


_GET /Users/{id}_

Retrieves a single user resource. The value of the {id} should be the user's corresponding CircleHD ID.  
  
  `GET /api/scim/v2/Users/U1A23BC4D HTTP/1.1  
Host: <your subdomain>.circlehd.com  
Accept: application/json  
Authorization: Basic nyzxSLInlhff5tOxuGpeC29iEe9c=`

\_\_

_POST /Users_

Creates a user. Must include the userName attribute and at least one email address. You may provide an email address in the userName field, but it will be automatically converted to a CircleHD-appropriate username.  
  
This example request body provides a detailed example of which attributes CircleHD uses, especially for the multi-valued attributes.  
  
`{ "schemas": ["urn:scim:schemas:core:1.0", "urn:scim:schemas:extension:enterprise:1.0"], "userName": "other_username", "nickName": "CircleHD_username", "name": { "familyName": "Last", "givenName": "First", "honorificPrefix": "Ms." }, "displayName": "First Last", "profileUrl": "`[`https://login.example.com/CircleHD_username`](https://login.example.com/CircleHD_username)`", "emails": [ { "value": "john.doe@example.com", "type": "work", "primary": true }, { "value": "some_other@email.com", "type": "home" } ], "addresses": [ { "streetAddress": "951 Mariners Island blvd", "locality": "Chicago", "region": "IL", "postalCode": "60613", "country": "USA", "primary": true }, ], "phoneNumbers": [ { "value": "555-555-5555", "type": "work" }, { "value": "123-456-7890", "type": "mobile" } ], "photos": [   
{ "value": "`[`https://photos.example.com/profilephoto.jpg`](https://photos.example.com/profilephoto.jpg)`","type": "photo" }, ], "roles": [ { "value": "Tech Lead", "primary": "true" } ], "userType": "Employee", "title": "Sales Manager", "preferredLanguage":"en_US", "locale": "en_US", "timezone": "America/Chicago", "active":true, "password":"sooopersec3et", "urn:scim:schemas:extension:enterprise:1.0": { "employeeNumber": "701984", "costCenter": "4130", "organization": "Chicago Cubs", "division": "Sales", "department": "Enterprise", "manager": { "managerId": "mgr@example.com" } } }`  
  


_PATCH /Users/{id}_

Updates an existing user resource, overwriting values for specified attributes. Attributes that are not provided will remain unchanged.  
  
Disabled users can be re-enabled by sending active attribute equal to true. The value of the {id} should be the user's corresponding CircleHD ID.  
  
`{ "schemas": [  
        "urn:scim:schemas:core:1.0"  
    ],  
    "id": "john.doe@example.com",  
    "active": true,  
    "emails": [  
        {  
            "value": "some@new.email.com",  
            "primary": true  
        }  
    ]  
}`  
  
__

_PUT /Users/{id}_

Updates an existing user resource, overwriting all values for a user even if an attribute is empty or not provided. If an attribute that had been set previously is left blank during a PUT operation, the new value will be blank in accordance with the data type of the attribute and the storage provider.  
  
__Deactivated users can be re-enabled by setting the active attribute to true. The value of the {id} should be the user's corresponding CircleHD ID.  
  
`{  
    "schemas": [  
        "urn:scim:schemas:core:1.0"    ],  
        "id": "john.doe@example.com",  
        "active": false,  
        "userName": "other_username",  
        "nickName": "CircleHD_username",  
        "name": {  
        "givenName": "First",  
        "familyName": "Last"  
        },  
        "title": "Ms.",  
        "emails": [  
        {  
          "value": "john.doe@example.com",  
          "primary": true  
         }  
        ],  
     "photos": [  
      {   
       "value": "https://some.image/url",  
       "type": "photo"  
       }  
      ]  
}`  


_DELETE /Users/{id}_

Sets a CircleHD user to deactivated and hides this user from all future requests. The value of the {id} should be the user's corresponding CircleHD ID.  
  
`DELETE /api/scim/v2/Users/100 HTTP/1.1  
Host: <your subdomain>.circlehd.com  
Accept: application/json  
Authorization: Basic nyzxSLInlhff5tOxuGpeC29iEe9c=`  


#### Groups

Groups are for organizing users in logical divisions across a workspace, such as by team or affinity. Group attributes are the details associated with a group. This feature is currently not supported in CircleHD’s scim gateway

_GET /Groups_

Not supported currently.

_GET /Groups/{id}_

Not supported currently.

_POST /Groups_

Not supported currently.

_PATCH /Groups/{id}_

Not supported currently.

_PUT /Groups/{id}_

Not supported currently.

_DELETE /Groups/{id}_

Not supported currently.

### Errors

Occasionally, interacting with CircleHD SCIM APIs may result in an error instead of the results you're expecting. CircleHD will make every attempt to respond with a descriptive error message that will help you figure out what went wrong and how to fix it.  


| Error | Description |
| :--- | :--- |
| bad\_email\_address | The email address provided does not exist or was poorly formatted |
| bad\_endpoint | The endpoint URL does not exist. |
| cannot\_modify\_owner | A site ownership can not be modified via SCIM, please use the CircleHD admin. |
| cannot\_modify\_gdpr | Users who have had their personal information forgotten under GDPR can not be modified. |
| cannot\_disable\_bot\_user\_with\_scim | The SCIM API can not be used to deactivate a bot user, this must be done via the bot admin. |
| cannot\_disable\_primary\_owner | The primary owner of a domain can not be disabled. If this user needs to be disabled, please make another team member the primary owner first. |
| invalid\_authentication | There's a problem with the OAuth token. It may not have been granted the proper admin scope or may not have been installed by an administrator. The token may also be malformed or not properly sent via an Authorization header with a type of Bearer. |
| invalid\_display\_name | The provided display name is not allowed. |
| invalid\_name\_specials | The provided display name is not allowed because it is using invalid special characters such as @. |
| invalid\_query | There's a problem with the filter parameter. Please check that the entities and operators are valid. |
| no\_such\_user | The user provided does not exist. |
| too\_many\_requests | The app is making too many requests over a short period of time. Please make fewer requests to stay within CircleHD's rate limits. |
| username\_required | This method requires a username parameter. |
| username\_taken | When provisioning a new user via SCIM, usernames must be unique. |
| username\_too\_long | The specified username is too long \(max length is 21 characters\). |

### SCIM Provisioning Limitations

* Users can not be permanently deleted from CircleHD, they can only be deactivated.
* Attempts to provision a user with a duplicate email address \(even if the existing user has been previously deactivated in CircleHD\) will fail. The existing user email address must be updated manually in CircleHD to free up the email to be re-provisioned.
* When creating a new user, if anything in custom profile is invalid, all profile fields will be dropped
* The SCIM API is rate limited. If your requests are being limited, an HTTP: 429 error will be returned.
* CircleHD does not store type for addresses. The type field will be used to determine which address is the "primary address" if the request does not specify one, however the type is not stored.

For questions: support@circlehd.com  


