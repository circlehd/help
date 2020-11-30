---
description: >-
  This article talk about Embedding and integrating videos from CircleHD to
  other systems such as LMS and SharePoint.
---

# Embedding Videos

## Embed Markup \(HTML\)

CircleHD supports embedding videos into other systems such as LMS, Wiki, Confluence and SharePoint. To get the embed markup click **sharing** below the video playback. 

![](../.gitbook/assets/share3.png)

![](../.gitbook/assets/share2.png)

  
The standard HTML Code looks like following.

```markup
<iframe allowfullscreen width="100%" height="320" frameborder="0" 
src="https://site.circlehd.com/embed/url?tok=xyz"></iframe>
```

{% hint style="info" %}
 The height and width can be modified to match the target container. Default height 320 is too small in most cases should be replaced.
{% endhint %}

### Embedding on a trusted sites.

By default users must be logged in to watch on the embed. If you have a trusted site, and you don't like to force the users to log-in before watching, you can enable trusted site under portal settings.

Users accessing iframe based embedding from these domains will not be prompted to login. However, the username will not show up in analytics if they have not previously logged into CircleHD

![](../.gitbook/assets/secure-embed.png)

{% hint style="info" %}
If you have multiple domains, wildcard domain names can be added.
{% endhint %}

