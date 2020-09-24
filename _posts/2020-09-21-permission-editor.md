---

title: "Permission editor on the admin ui"
author: [pusztaienike]
image: "../img/posts/permission_editor.jpg"
tags: [sensenet, permission]

---

"Nobody can hurt me without my permission. /Mahatma Gandhi/"

---

In the IT world you often handle sensitive data, which you don't want to share with the whole universe. But how you can hide those contents from outsiders? What if you would like to share those things only with a specific group of users? Or other data with another group? 

Of course there is a common solution for that: permission system. Almost every software has permissions which handle what users can see or do.

I think most of us use any social network. You may search for a person and you cannot see her/his photos, after you apply a friend request everything change.
You see more than ever. Or what about your company? If you are not the boss I am sure that your company has datas which you do not have the sufficient permission.

Permissions are everywhere. And of course sensenet has its own permission system as well. On the new admin-ui gui we did not have any surface to handle these permissions. Till now. 🕛 In the last couple of weeks we have tried to design and implement the simplest, easiest to use **permission editor**.

## Customize it as you want 🔧🔨

sensenet has a lot of built-in permission and we also keep some for your special needs:  Custom01, Custom02, etc. You can also group these permissions for the permission editor dialog as you want. The related settings file is available under Setup menu / Permission.settings.

The default settings are the following:

```{
   "groups":[
      {
         "Read":["See", "Preview", "PreviewWithoutWatermark", "PreviewWithoutRedaction", "Open"]
      },
      {
         "Write":[ "Save", "AddNew", "Delete"]
      },
      {
         "Versioning":["OpenMinor", "Publish", "ForceCheckin", "Approve", "RecallOldVersion"]
      },
      {
         "Advanced":["SeePermissions", "SetPermissions", "RunApplication"]
      }
   ]
}
```

On the permission editor dialog you can see the groups and permissions based on these settings. 

<p align="center">
<img src="/img/posts/permission_groups.png">
</p>

## How to use it? 🎮

Select a content from your repository, right-click on it and select 'Set permissions' from the dropdown. On the permission view you can check the entries which has inherited or set permissions. Selecting an entry makes the permission editor dialog open.

On the dialog turn the switchers to on/off to enable/disable a permission.  On groups there are also switchers as well: you can easily enable/disable all of the permission under the selected group... and there is the king of kings: Full access 👑 (you can turn on/off all permissions)

Some permissions are disabled because they are inherited and you cannot override them. The changes only apply on clicking Submit button so for your comfort there is also a reset button to restore the unsaved changes.

<p align="center">
<img src="/img/posts/permission_how_to_use.gif">
</p>

## Additional features 💄👓👜

**Make content public/private**

If you would like to share your content (content can be almost anything, cause in sensenet everything is a content) with somebody e.g. from another company who has no authority to your repository you can do it easily by clicking on "Make content public" button. If you change your mind reverting this is easy as it was to set.

<p align="center">
<img src="/img/posts/permission_make_public.gif">
</p>

**Assign new permission**

If you would like to add permission for someone who has no permisison at all on this content you can do it with assign new permission button. Select the user who needs the rights and turn on/off the switchers 😉

<p align="center">
<img src="/img/posts/permission_assign_new.gif">
</p>

**Local only**

There are cases however when you do not want child content to inherit a permission entry. For example you want to allow certain users to see a content (e.g. a Content List) but you do not want them to be able to see content that were added to that list. You can mark the permission entry as 'local-only' to avoid permission inheritence.
On permission view we mark these local-only entries with an icon.

<p align="center">
<img src="/img/posts/permission_local_only.gif">
</p>


**Force relations**

Some of the built-in permissions requires to allow other permission(s). E.g: If you would like to set Preview permission to an entry it requires to have See permission as well. You don't need to handle these relations cause it is automatic in the background. Setting the Preview permission will set See permission as well.

<p align="center">
<img src="/img/posts/permission_force_relations.gif">
</p>


## Must read 📚🔖

More details about our permission system:

[Document level Permissions](https://docs.sensenet.com/concepts/user-and-permission-management/02-document-level-permissions)

[Role based Permissions](https://docs.sensenet.com/concepts/user-and-permission-management/03-role-based-permissions)

[Custom Roles and Permissions](https://docs.sensenet.com/concepts/user-and-permission-management/04-custom-roles-and-permissions)