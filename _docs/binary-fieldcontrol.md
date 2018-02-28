---
title: "Binary Field Control"
source_url: 'https://github.com/SenseNet/sensenet/blob/master/docs/binary-fieldcontrol.md'
category: Development
version: v6.0
tags: [binary, file, field control, field]
description: The Binary Field Control is a Field Control that handles Binary Fields and provides an interface to modify binary data of a Content.
---

# Binary Field Control

The Binary Field Control is a Field Control that handles [Binary Fields](/docs/binary-field) and provides an interface to modify binary data of a Content.

<img src="https://raw.githubusercontent.com/SenseNet/sensenet/master/docs/images/ReferenceWiki_BinaryFieldControl1.png" style="margin: 20px auto" />

With Binary Field Control the binary data of a Content can be added/modified. Depending on the configuration of the Field and the Content Type and extension, the control is rendered as a textarea where you can edit the binary manually or as a fileupload control allowing you uploading a new file. By default an upload control is rendered. A textarea is rendered when:

- the displayed Content is a [Content Type](/docs/content-type,md),
- the displayed Content has an extension that is included in the web.config's *EditSourceExtensions* entry of the <portalSettings> section,
- otherwise when the *IsText* property in the underyling [Binary Field's](/docs/binary-field) [Field Setting](/docs/field-setting) is set to true.
When a textarea is rendered it can be displayed as a highlighted editor of bigger size using the FullScreenText property.

## Supported Field types

- [Binary Field](/docs/binary-field)

## Properties

- **FullScreenText**: (optional) renders the textarea in full screen for editing, without file upload control.

## Templates

Binary field control renders the name of the assigned file as a hyperlink in Browse mode. In Edit mode a fileupload control or a textarea control is rendered.

### Browse view template

```csharp
<%@  Language="C#" %>
<%@ Import Namespace="SenseNet.Portal.UI.Controls" %>
<a href='<%# ((Binary)Container).Field.Content.Path %>'><%# ((Binary)Container).Field.Content.DisplayName %></a>
```

### Edit view template

```csharp
<%@  Language="C#" %>
<asp:TextBox ID="BinaryTextBox" runat="server" TextMode="MultiLine" CssClass="sn-ctrl sn-ctrl-textarea" Rows="50" Columns="100" />
<asp:FileUpload CssClass="sn-ctrl sn-ctrl-upload" ID="FileUploader" runat="server" Visible="false" />
```

## Examples

### Simple example

```html
   <sn:Binary ID="BinaryCtrl" runat="server" FieldName="Data1" />
```

This next example displays the Field Control for editing in full screen.

```html
   <sn:Binary ID="BinaryCtrl" runat="server" FieldName="Data1" RenderMode="Edit" FullScreenText="true" />
```

### Templated example

```html
   <sn:Binary ID="BinaryCtrl" runat="server" FieldName="Data1">
      <EditTemplate>
         <asp:TextBox ID="InnerControl" runat="server" TextMode="MultiLine"></asp:TextBox>
         <asp:FileUpload ID="FileUploader" runat="server" Visible="false" />
      </EditTemplate>
   </sn:Binary>
```