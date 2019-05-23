---
description: This page is a guidance for how to enable SCIM integration with CircleHD
---

# SCIM

## **SCIM Overview**

The System for Cross-domain Identity Management \(SCIM\) specification is designed to make managing user identities in cloud service providers easier. Its intent is to reduce the cost and complexity of user management operations by providing a common user schema and extension model, as well as binding documents to provide patterns for exchanging this schema using standard protocols.

### **Model**

SCIM 2.0 is built on an object model where a Resource is the common denominator and all SCIM objects are derived from it. It has id, externalId and meta as attribute and RFC7643 defines User, Group and EnterpriseUser that extends the common attributes. Read more at  [https://tools.ietf.org/html/rfc7643](https://tools.ietf.org/html/rfc7643)  

![CircleHD Cloud Identity Security Architecture](https://lh5.googleusercontent.com/X1W-SYHz3kaola9E-usJvcpMuB9Ma4M2iMaSEWcTut3fs5WpjRK4PlWnUwK0n2zZ7iWphxSyCWBtdxtJSP2-BppUpTP6P5BCHUrF-xNcYmJnoBM4O4cxQd9IZ9JZtQfO_fJvGF4)

### **SCIM endpoints**

**The SCIM API is RESTful and the endpoint URLs are different than other CircleHD API endpoints.**  


