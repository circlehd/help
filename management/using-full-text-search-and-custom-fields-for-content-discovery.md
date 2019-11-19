# How to use Full Text Search and custom fields for Content Discovery

CircleHD provides a smart search option to navigate to required content quickly and easily among hundreds or thousands of videos and slides. It uses full text indexing within the actual content and also associated tags, metadata, custom fields. ****

### **What is Full Text Search?**

When the total number of media to search is potentially large, full text search allows users to narrow down the results to the most relevant content. 

During Indexing, we make sure to ignore irrelevant stop words \(e.g. "the", “is”, etc. \) which are not meaningful in searching. CircleHD also implements language-specific stemming on the indexed words. For example, the words "fly", "flying", and "flew" will be recorded in the index under "fly", therefore you can focus on content that is more meaningful to you when you most need them.

![Grid View for Search Results](../.gitbook/assets/image%20%2821%29.png)

![List View for Search Results](../.gitbook/assets/image%20%2818%29.png)

In advanced search, if a content piece is a binary file, such as Videos, Audios, Slides, etc. It will gather all words within the binary file and add them as the indexes. 

CircleHD also allows user to add custom fields to be associated with each uploaded and created content, whose value can be indexed to support enhanced filtering of content. 

Custom Fields also makes it easier for admins to create AI filters and reports which can be used to further enhance the user experience and user flow within the portal.

![Edit Video / Slideshows Metadata](https://lh3.googleusercontent.com/fR83Cg4_t_iM7LpkN-xhhp7qwZr_LQbgSRWMyidy4ckDPaYF9F6vRR5cuV1IdLoFxeVzdu1xYW6_ySj8hz2isCHLuswTaMa5w4XF3D0Vgb0YaMgPc_707AscocN12yTQ2nhzW0u2)

### **How to define Custom fields and use them for smart search?**

Creating custom fields in CircleHD is an admin only option, it allows them to create new fields and types that can be associated with all content pieces within the portal. Currently, this is assigned global to all content pieces within the portal. So whenever an end user edits content within the portal, he will have the option of setting a value for the custom fields.  
  
**Steps to create a new custom field.**

1. Click on the top right Profile menu drop down. Select Portal Settings

![Profile Drop Down Menu](https://lh3.googleusercontent.com/kSFzgxj1bm60RbkQLpR8yCTBANXQQtZP7TlR4RBi_aPd9Vv_4E2E2l4rSHD4d931ZbESw6-kWgflfSuUQyvNcN8vVvQeLPYu9PxUyTMSXfkYTntBLEJq1OAo_AMcznnbRm_DlhLO)

2. Click on Configuration =&gt; Custom Fields in the left menu

![Custom Fields Admin Settings](https://lh4.googleusercontent.com/VWrGzGlYnWLV_v0QD3YNPn-JwHF_uR7FXxaNh-sQ17gpDc86FaSq90nk_ZQiaBv5fUTN6ddoJ2eNkNeT7d0RrTkXvzIf-mqs7Fy5vWKCiVS_td3oP8SkUlyNZsCZDrBsQTuY8IXe)

3. Click on “Add New Field” button, you will see a popup to enter custom field values. 

4. Enter the Name of the custom field, select type and enter values in the text box below if its an option type or a multiple option type.

![Editing Custom Fields](https://lh3.googleusercontent.com/c45CpnDy9E031-voyLFvmiTMPxV7rCqBcIe2bN7D0iLLUwS5YwT9koEtajqTjkvFi3wcqtszAQ67D2p0NTnJeb6u0XovINWUTUyMv0cMmSbO-uW4_5WRT7s3Dijh4zQC2UF5xOxn)

5. If custom field values are set for a content piece, then CircleHDs smart search will index those values and you would be able to use this to narrow down or filter results further.

![Using Custom Fields to filter Search Results](../.gitbook/assets/image%20%2814%29.png)

