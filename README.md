
# 🎥 Power Apps Video Playback – No SharePoint, No Hassle

![Power Platform](https://img.shields.io/badge/Microsoft-Power%20Platform-6A5ACD?logo=powerapps&logoColor=white)
![Power Apps](https://img.shields.io/badge/Power%20Apps-CanvasApp-purple?logo=powerapps)
![Dataverse](https://img.shields.io/badge/Dataverse-Attachments-green)
![Azure Blob](https://img.shields.io/badge/Azure-BlobStorage-blue)

> This repo demonstrates two low-code techniques to play video files in Power Apps —  
> one using native Dataverse attachments, and another using dynamic Azure Blob URLs —  
> without relying on SharePoint or Power Automate.

---

## 🔥 Two Powerful Ways to Stream Video Files in Power Apps

- ➡️ Without using SharePoint or OneDrive  
- ➡️ Without writing complex flows or SAS logic

---

## 🧩 Real Dev Problem

> "I stored my video file in Dataverse.  
> How do I just **play it** inside Power Apps without sending it to SharePoint or Azure Blob?"

- Sounds familiar? We've all been there.  
- This repo solves that problem with **two easy, production-ready techniques**.

---

## ✅ Solution 1: Play Video Directly from Dataverse Attachment

> Upload ➜ Store in Attachment column ➜ Play using native Power Fx


### 🛠 How to Implement:

```
Gallery1.Selected.Attachment.Value
```

💡 Explanation:

Gallery1 → The gallery displaying records that contain attachments

.Selected → The item you’ve clicked/selected in the gallery

.Attachment.Value → Refers to the fileimageurl, which is a temporary, secure, session-bound hyperlink to the uploaded file in the Dataverse table

This formula directly feeds the URL into a Video control:

```
Video1.Media = Gallery1.Selected.Attachment.Value
```
#  🔧 Steps:
Use a form with attachments enabled in Dataverse

Show uploaded files using a Gallery

Add a Video control and set the Media property as shown above

✔️ This pulls the fileimageurl behind the scenes
✔️ The video streams instantly inside the app

🔒 Note: Works perfectly for internal authenticated users (not public links)

---
# 📸 Sample UI

- ![Video playback from Dataverse](https://github.com/vasavisuggala/PowerApps-dataverse-or-blob-video-player/blob/screenshots/dataverse-video-ui.png)


## ⚙️ Solution 2: Play Video from Azure Blob – with Just a Formula
Already storing files in Blob? You can still stream videos dynamically using just one formula.
```
"https://<storageaccount>.blob.core.windows.net/<container>/" & 
    ThisItem.Name & 
    "?<sas_token>"
```
- ✔️ Works for long-term storage, large files, or external users
- ✔️ URL can be dynamically built using metadata stored in Dataverse

## 🎯 Use Cases

- Field inspection apps capturing video evidence

- Internal feedback or demo portals with video uploads

- Training, knowledge-sharing, and case documentation

- Low-code POCs requiring media handling without storage complexity

## 🧠 When to Use What?

| Scenario                              | Use Solution #1 | Use Solution #2 |
| ------------------------------------- | --------------- | --------------- |
| Internal business app                 | ✅               |                 |
| Temporary session-based playback      | ✅               |                 |
| Need public or anonymous video access |                 | ✅               |
| Blob storage already used in app      |                 | ✅               |
| Want zero dependencies, simple setup  | ✅               |                 |


🙌 Credits
Special thanks to  ![Dileep](https://www.linkedin.com/in/dileepsuggala/)

