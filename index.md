**Table of Contents:**

## Introduction

### About Hippo Video

Hippo Video’s SDK allows any organization to add **async video messaging** to its platform and applications. While everyone agrees that video messages can increase the engagement with the viewers multifold, not everyone can build a video messaging platform. Embedding Hippo Video’s SDK into your product can get you up and running within a short time thus providing your audiences with a great experience of recording videos.

Since videos can be used by all functions within an organization, every platform that is built for Sales, Marketing, Support, and Internal Communication can integrate with Hippo Video through our SDK.

## Getting Started

### Setting up Account

1. Signup to create an account with Hippo Video. It's free: [https://www.hippovideo.io/users/sign_up](https://www.hippovideo.io/users/sign_up)
2. Go to the Integrations [https://www.hippovideo.io/settings/integrations](https://www.hippovideo.io/settings/integrations) page.
3. Click on the  button near the Generic Embed Widget
4. Now copy the script code and place it inside your **body tag**. Preferably at the end.

```jsx
<script>
var s = document.createElement("script"); 
s.src = "[https://s3.amazonaws.com/hippovideo-embed-widget/js/hippovideo-embed-script.js](https://s3.amazonaws.com/hippovideo-embed-widget/js/hippovideo-embed-script.js)";
window.setDigestOnStart = true;
s.async = true;
window.hippovideoDigest = "BSp91ll2rhN9vBReg_kMo2eEblxvc4oe4X_toBzWRnF"// this code will change for you //;
window.hvintegtype = "generic_embed";
window.hippoWidget={loadedCallbacks:[],isLoaded:false,onLoad: function(callback)
{if(window.hippoWidget.isLoaded==true)callback();
else window.hippoWidget.loadedCallbacks.push(callback);}};
document.head.appendChild(s);
</script>

```

1. To record the screen, your user base needs to have the Hippo Video's Chrome Extension. This link should help: [https://chrome.google.com/webstore/detail/hippo-video-video-and-scr/cijidiollmnkegoghpfobabpecdkeiah](https://chrome.google.com/webstore/detail/hippo-video-video-and-scr/cijidiollmnkegoghpfobabpecdkeiah)
2. Place the below html div in your page where you want the Hippo Video Record to appear. Keep the same div id but you can add style/css to this Record button.

```jsx
<div id="hv-generic-embed-input">
<input type="text">
</div>
```

You may find summary in the following video:

[https://h-vd.io/RPE2q9WQ](https://h-vd.io/RPE2q9WQ)

### Recorder API

**Start Recording**

You can customize the recording options.

```jsx
var recordingConfiguration = {
screenRecord: true,
audio: true,
webCam: true,
systemAudio: true,
resolution: "720",
separateLayer: false,
initiator: 'generic_embed'};
window.hippoWidget.startRecording(recordingConfiguration)
```

- 'audio' option enables the mic recording
- 'systemAudio' enables the system audio like any application or browser tab playing any music.

**Stop Recording**

```jsx
window.hippoWidget.stopRecording()
```

**Logs and Event Handling**

```jsx
window.hippoWidget.on(eventname, callback);
```

**Events**

<img width="1516" alt="image" src="https://user-images.githubusercontent.com/110969744/183869692-04de73e2-4d50-4222-a1f0-7849bb46746d.png">



### Import API

```jsx
window.hippoWidget.import()
```

**Params**

- **title** - Video title
- **URL** - Downloadable URL of the video
- **email** - email of the user
- **api_key** - API Key of the user

**Response**

```jsx
{
	"status": 200,
	"code": 200,
	"video_id":1412089,
	"share_url": "[https://www.hippovideo.io/video/play/KQf5MPDupD2qFi4U_LYoo436nEf7gilJIW0I_Pn1Ia8](https://www.hippovideo.io/video/play/KQf5MPDupD2qFi4U_LYoo436nEf7gilJIW0I_Pn1Ia8)",
	"embed_url": "[https://www.hippovideo.io/video/embed/KQf5MPDupD2qFi4U_LYoo436nEf7gilJIW0I_Pn1Ia8](https://www.hippovideo.io/video/embed/KQf5MPDupD2qFi4U_LYoo436nEf7gilJIW0I_Pn1Ia8)",
	"thumbnail_preview": "[https://hippolms-storage.s3-accelerate.amazonaws.com/wiz/videos/previews/KQf5MPDupD2qFi4U_LYoo436nEf7gilJIW0I_Pn1Ia8.gif](https://hippolms-storage.s3-accelerate.amazonaws.com/wiz/videos/previews/KQf5MPDupD2qFi4U_LYoo436nEf7gilJIW0I_Pn1Ia8.gif)",
}
```

- **share_url** -  Shareable video link.
- **embed_url** - Link to embed the video.
- **thumbnail_preview** - Thumbnail of the video with a play icon (you can share the thumbnail linking it to your video).

### **Reports API**

This API provides two types of reports:

1. **Reports for a video**
    
    
    **Params**
    
    - **email** - email of the user
    - **api_key** - Api Key of the user
    - **video_id** - id of the video
    
    **Response**
    

```jsx
{
    "status": 200,
    "id": 988,
    "total_plays": 13,
    "total_page_loads": 15,
    "unique_users": 10,
    "avg_watch_rate": 85,
    "actions": {
        "no_of_actions": 111,
        "annotations": 4,
        "call_to_actions": 19,
        "forms": 6,
        "end_screens": 3,
        "questions": 5,
        "comments": 8,
        "reactions": 63,
        "replies": 3
    },
    "watch_rate": {
        "0": 0,
        "25": 3,
        "50": 2,
        "75": 1,
        "100": 5
    },
    "popular_region": "Houston, Texas",
    "plays_in_popular_region": "1 plays from Houston, Texas"
}
```

- **id** - Video ID
- **total_page_loads** - Number of times the shared link is opened.
- **total_plays** - Number of times the video has been played out of total page loads.
- **unique_users** - Number of unique users that have played the video.
- **avg_watch_rate** - The overall percentage (total duration watched / total plays * video duration)
- **actions** - (annotation, CTA, lead generation forms, etc.)
- **no_of_actions** - Total number of actions.
    - **annotations** - Number of clicks on annotations.
    - **call_to_actions** - Number of clicks on CTA.
    - **forms** - Number of clicks on lead generation forms.
    - **end_screens** - Number of clicks on playlist.
    - **questions** - Number of clicks on custom poll.
    - **comments** - Total number of comments on the video.
    - **reactions** - Total number of reactions on the video.
    - **replies** - Number of replies to the comments.
    
1. **Viewer profile reports**
    1. **Based on Video**
        
        This report offers all the details of a video such as the number of views, watch rate, viewer location, and the viewer's engagement on a particular video. To get the reports, you must call the link below.
        
        **Params**
        
        - **email** - email of the user
        - **api_key** - API Key of the user
        - **user_email (optional)** - mail id of the lead
        - **video_id (optional)** - id of the video
        
        Note: You can either provide user_email or video_id. They are mutually exclusive. If you'd like to know how a particular video is performing, then enter video_id.
        
        **Response**
        
        ```jsx
        {
        "status": 200,
        "viewer_profile": [
            {
                "video_id": "988",
                "email": 'michael.clark@icc.com',
                "viewer_name": 'Michael Clark',
                "ip": "188.XXX.29.XXX",
                "last_viewed_time": "31/12/2018 02:23 AM",
                "location": "Sydney, Australia",
                "device": "DESKTOP",
                "os": Macintosh,
                "browser": Chrome,
                "referer_url": "<https://www.google.co.in/>",
                "precentage_played": 95,
                "views": 2
            }
        ],
        "load_more": false,
        "page": 1,
        "next_page": 2
        }
        
        ```
        
    2. **Based on Lead’s Email**
        
        This report offers all the details for a particular lead’s email address such as the number of videos watched, watch rate, lead's location, and their engagement on the videos.
        
        **Params**
        
        - **email** - email of the user
        - **api_key** - API Key of the user
        - **user_email (optional)** - mail id of the lead
        
        Note: This API is the same as the report based on the video, except the ‘user_email’ param should be passed instead of ‘video_id.’
        
        **Response**
        
        ```jsx
        {
            "status": 200,
            "viewer_profile": [
                {
                    "video_id": "999",
                    "email": "joebrown@google.com",
                    "viewer_name": "Joe Brown",
                    "ip": "188.XXX.29.XXX",
                    "last_viewed_time": "09/01/2019 12:27PM",
                    "location": " NA ",
                    "device": "DESKTOP",
                    "os": "Macintosh",
                    "browser": "Chrome",
                    "referer_url": "https://mail.google.com/mail/u/#sent/16831654c41cc10a",
                    "precentage_played": 36,
                    "views": 1
                },
                {
                    "video_id": "937",
                    "email": "joebrown@google.com",
                    "viewer_name": "Joe Brown",
                    "ip": "188.XXX.29.XXX",
                    "last_viewed_time": "19/10/2018 12:25PM",
                    "location": "Naples, ITALY",
                    "device": "DESKTOP",
                    "os": "Macintosh",
                    "browser": "Chrome",
                    "referer_url": " NA ",
                    "precentage_played": 100,
                    "views": 1
                }
            ],
            "load_more": false,
            "page": 1,
            "next_page": 2
        }
        ```
        
        - **video_id** - ID of the video.
        - **email** - Email address of the lead.
        - **viewer_name** - Name of the lead.
        - **ip** - Masked IP of the lead.
        - **last_viewed_time** - Time at which the lead has watched the video.
        - **location** - Geographical location of the lead.
        - **device** - Device used by the lead to watch the video.
        - **os** - Operating system of the device in which the lead has watched the video.
        - **browser** - The browser in which the lead has watched the video.
        - **referer_url** - The address of the webpage where a person clicked a link that sent them to your video.
        - **percentage_played** - Percentage of video watched.
        - **load_more** - By default, the number of videos in an API call is 10. P.S: load_more is true if it has more results left.
        - **page** - The current page number.
        - **next_page** - The number of the next page.
        
        The above responses are success cases. In case, any errors occur you’ll see an [error response](https://help.hippovideo.io/support/solutions/articles/19000095987-error-page).
        

### **Webhooks**

Webhook helps you to get notified as soon as someone takes a desired action on your platform. A Webhook enables an application to send automated messages or information to another application, whenever an event takes place, in real-time. Basically, a Webhook is a medium that enables apps to communicate with each other and share data.

**Available events in Webhook**

Any change that occurs on an application or a system is considered an event. Here are some default events that we provide:

1. **Viewing Session**
    
    Find out who watched your video. When someone clicks on your video, we’ll notify you of the watch rate along with other user details (only if the viewer has logged in before watching your video).
    
    *Example Response:*
    
    ```jsx
    {
      "hook": {
        "uuid": "fb9f6d19-921f-48c5-9a10-69c39e5fa13c"
      },
      "eventName": "VideoPlayedSessions",
      "eventTimestamp": "1542364983607",
      "VideoPlayedSessions": {
    	    "media": {
    		      "videoId": 444076,
    		      "thumbnail": "https://hippolms-storage.s3-accelerate.amazonaws.com/wiz/videos/thumbnails/21594/da2f955a-5410-489b-a10c-43b7d0a192af_play.jpg",
    		      "name": "Pro edit full flow",
    		      "shareUrl": "https://www.hippovideo.io/video/play/mp1lhvzM9gyOY1mg19Fl2Q",
    		      "embedUrl": "https://www.hippovideo.io/video/embed/mp1lhvzM9gyOY1mg19Fl2Q",
    		      "duration": 171.689
    	    },
    		   "percentagePlayed": 100,
    		   "email": "support@hippovideo.io"
      },
      "metadata": {
    	    "account_id": "24880"
      }
    }
    ```
    

1. **Video Created**
    
    We notify you whenever someone creates a video on your platform.
    
    *Example Response:*
    
    ```jsx
    {
      "hook": {
        "uuid": "598210b8-e373-48eb-ac3f-4b8f08fa8066"
      },
      "eventName": "VideoCreated",
      "eventTimestamp": "1542032461018",
      "VideoCreated": {
        "media": {
          "videoId": 834871,
          "thumbnail": "https://hippolms-storage.s3-accelerate.amazonaws.com/wiz/videos/thumbnails/v2/FCNN4s7tKjCOaecmg6hjzw_play.jpg",
          "name": "Hey Ashley",
          "shareUrl": "https://www.hippovideo.io/video/play/FCNN4s7tKjCOaecmg6hjzw",
          "embedUrl": "https://www.hippovideo.io/video/embed/FCNN4s7tKjCOaecmg6hjzw",
          "duration": 13.76
        }
      },
      "metadata": {
        "account_id": "60753",
        "created_by": "support@hippovideo.io"
      }
    }
    ```
    

1. **CTA**
    
    Get notified whenever your viewers click on a Call to Action (CTA) in your video.
    
    *Example response:*
    
    ```jsx
    {
      "hook": {
        "uuid": "ffc5bf89-16e8-428d-92e8-a94016b5e8f2"
      },
      "eventName": "VideoCTA",
      "eventTimestamp": "1542191371256",
      "VideoCTA": {
        "media": {
          "videoId": 809864,
          "thumbnail": "https://hippolms-storage.s3-accelerate.amazonaws.com/wiz/videos/thumbnails/v2/c9ryLBsotAVJITn12NZIKg_play.jpg",
          "name": "A",
          "shareUrl": "https://www.hippovideo.io/video/play/c9ryLBsotAVJITn12NZIKg",
          "embedUrl": "https://www.hippovideo.io/video/embed/c9ryLBsotAVJITn12NZIKg",
          "duration": 146.912
        },
        "ctaUrl": "https://www.hippovideo.io/video/cta/809864",
        "email": "support@hippovideo.io"
      },
      "metadata": {
        "account_id": "60753"
      }
    }
    ```
    

1. **CTA Lead Generation**
    
    Get notified with your lead's information. Whenever someone fills a form that you have embedded in your video, you’ll receive an instant notification, with their details. You can also choose to update your lead's information straight away into your CRM platform.
    
    *Example response:*
    
    ```jsx
    {
      "hook": {
        "uuid": "681dc0a4-1baa-497e-b9c4-674a66924f88"
      },
      "eventName": "VideoLeadGenaration",
      "eventTimestamp": "1542020582260",
      "VideoLeadGenaration": {
        "media": {
          "videoId": 826784,
          "thumbnail": "https://hippolms-storage.s3-accelerate.amazonaws.com/wiz/videos/thumbnails/v2/U4GZz3AFN8vHcplqEYl7Fg_play.jpg",
          "name": "Sales demo",
          "shareUrl": "https://www.hippovideo.io/video/play/U4GZz3AFN8vHcplqEYl7Fg",
          "embedUrl": "https://www.hippovideo.io/video/embed/U4GZz3AFN8vHcplqEYl7Fg",
          "duration": 139.203
        },
        "firstName": "Varun",
        "lastName": "Ch",
        "email": "support@hippovideo.io",
        "phone": "2132121"
      },
      "metadata": {
        "account_id": "24880"
      }
    }
    ```
    

1. **CTA Annotation**
    
    Do you have an annotation that directs your viewers to your website? How do you track who clicked on your annotation? Don’t worry. We notify who’s clicking on your annotation along with the viewer’s information.
    
    *Example response:*
    
    ```jsx
    {
      "hook": {
        "uuid": "e72c91f5-9c7a-4419-bd1e-c1d3d17ae3ef"
      },
      "eventName": "VideoAnnotation",
      "eventTimestamp": "1541759939981",
      "payload": {
        "VideoAnnotation": {
          "videoId": 814440,
          "thumbnail": "https://hippolms-storage.s3-accelerate.amazonaws.com/wiz/videos/thumbnails/v2/cS-qeih4T7LkWzhQnYbzVA_play.jpg",
          "name": "Hey, How are you?",
          "shareUrl": "https://www.hippovideo.io/video/play/cS-qeih4T7LkWzhQnYbzVAhttps://www.hippovideo.io/video/play/cS-qeih4T7LkWzhQnYbzVA",
          "embedUrl": "https://www.hippovideo.io/video/embed/cS-qeih4T7LkWzhQnYbzVA"
        },
        "annotationText": "Google",
        "annotationUrl": "https://www.google.co.in/",
        "annotationClickedTime": 0,
        "email": "support@hippovideo.io"
      },
      "metadata": {
        "account_id": "60753"
      }
    }
    ```
    

**Secret Key**

On the other hand, anyone with your server URL can send you data. To verify the data source, we suggest you create a secret key of your choice. So that whenever you receive information from Hippo Video, you can verify whether the data is from us.

It works this way - Every time you receive data from our side, we also provide Hippo Video signature in the request. Using the signature, you can verify the data authenticity by checking it at your end. We’ll generate an HMAC hexdigest of the POST body, using the secret_key that you created, while configuring your webhook. The generated hexdigest will be shared with you along with the event data. If you have any questions, contact us at support@hippovideo.io

### Sandbox Environment

[https://codesandbox.io/s/hopeful-mountain-kp2b0?file=/src/index.js](https://codesandbox.io/s/hopeful-mountain-kp2b0?file=/src/index.js)

### Live Example

[https://www.hippovideo.io/embed-sample-form.html](https://www.hippovideo.io/embed-sample-form.html)

## Why Hippo Video

### Key USP's

- **Screen, Audio, and Webcam Capture**
- **Instant Video Playback**

Our Player is lightweight, aesthetically pleasing, and provides a better experience! Your videos look the best in this player. You can play the video at multiple speeds, 1.5X or even 2X.

Get a glimpse of all the video details like the video duration and video name in the thumbnail itself. This way, your audience knows what exactly they can look forward to in the video.

![new-feature-update-.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/40242a81-609a-45e4-9b9e-ec0bef5be4ea/new-feature-update-.png)

- **Teleprompter**

Hippo Video allows you to read the script directly from the screen and record professional videos. This way, anyone can get started with videos faster, even if they have zero experience recording videos. You can set up separate scripts for each category so when anyone is recording videos, they would know which script they should go for, making it easier for them to prepare scripts, saving a lot of time.

![ezgif.com-gif-maker (4).gif](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/85d4864a-3be9-46a4-aa62-8702ed6b9e1d/ezgif.com-gif-maker_(4).gif)

- **Markup Tools**

Draw attention to important information with the Highlight option. Draw and write any text on your video. Change the color of the highlighter according to your preference. The Focus option will allow you to focus on a particular portion of a video seamlessly. This way, you can drive attention to certain parts of the document or anything you are showcasing.

With the help of the cursor feature, you can make sure your audience travels along with you while watching your video. This way, they are both involved and engaged throughout the video.

![ezgif.com-gif-maker (3).gif](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/679f7c7c-ebe7-4c5a-83c6-dfe6a2aeed69/ezgif.com-gif-maker_(3).gif)

- **Circular Webcam**

Hippo Video offers different webcam shape options. You can change your webcam shape with just a click. You can either choose a circular webcam or a rectangular webcam. A circular webcam enhances the look and feels of your videos.

![ezgif.com-gif-maker (1).gif](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/39c0d710-1fcd-4401-95b0-20955ba2f27c/ezgif.com-gif-maker_(1).gif)

- **Extension-less Recording**

With Hippo Video’s extension-less recording option, you can record videos seamlessly without any additional setup. This can be done in any browser like Chrome, Firefox, Opera, Edge(latest version 80+), and Safari. Also, there is no IT/Compliance permission needed in enterprises to install the Chrome Plugin for recording.

![screen1.gif](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/bcf86f03-5f1e-458a-9405-7b606b8773b1/screen1.gif)

- **Facial Cues and Lighting**

Hippo Video allows you to quickly test your webcam before you start recording videos. Get information on your webcam lighting, the frame rate, resolution, and webcam quality. This webcam test allows you to set up your webcam the right way to deliver the best videos.

- **Reply With Video**

[CAM_2b.webp](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/bbfc94a2-349e-41e2-8a56-b6a99023ac25/CAM_2b.webp)

Hippo Video lets you share your videos with the world and with the video reply option, anyone can record videos as a response to your videos. You don’t have to be signed up with Hippo Video to record videos with Hippo Video “Video Reply” option. Be it feedback from your audience or answering a question, anyone can record a video reply within minutes.

### Features in Roadmap

![ezgif.com-gif-maker.gif](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c5093f0a-b395-4c26-8b43-70b7f17fd86d/ezgif.com-gif-maker.gif)

- **Video Stitching**

With Hippo Video, you can now record multiple videos and stitch them together as a single video. You can choose to record various chapters, questions, or even feedback-related answers all at one go. Video stitching leads to better productivity and saves a lot of time.

- **Timeline Comments & Emojis**

![ezgif.com-gif-maker (5).gif](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/644623dd-4294-480e-8b48-b572b2cd20ca/ezgif.com-gif-maker_(5).gif)

Timeline comments & Emojis - Along with the new sleek video player, Hippo Video also provides features like emoji-based likes on the timeline that helps you to express yourself through reactions. The player also has the ability to capture comments on the timeline which makes it easy for your audience to react to a particular chapter in the video and deliver feedback then and there while watching the video.

![ezgif.com-gif-maker (6).gif](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c6e13ecd-9928-4dd4-a5da-fded36a641f2/ezgif.com-gif-maker_(6).gif)

- **Virtual Background**

With Hippo Video’s virtual background feature, you can now change your video background and record professional videos. You can select the background of your choice or also choose to add any images as the video background.

![ezgif.com-gif-maker (2).gif](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ede83798-9412-4122-b022-2833d3771a14/ezgif.com-gif-maker_(2).gif)

## **Infrastructure and Compliance**

### Infrastructure

- Hosted on AWS VPC
- High Availability through multiple replication
- AWS’s network security against DDoS and Port Scanning

### **Encryption and Scalability**

- Amazon’s RDS for DB redundancy
- Auto Scaling Infrastructure
- AES 256 encryption
- TLS v1.2 for data transmission

### **Authentication**

- Role-Based Access Control
- OAuth v2.0 for user authentication (Can be integrated with Azure AD)
- Hashed Passwords
- Password protected Videos

### **Commitment to Compliance**

- SOC 2 Type II Certified
- ISO 27001 Certified
- Infrastructure Vendor is ISO 27001, SOC 2 certified
- Payment Gateway Vendor is PCI DSS, SOC 1, SOC 2, ISO 27001 certified

## Staying informed[](https://docusaurus.io/docs#staying-informed)

- Help Articles:

[https://help.hippovideo.io/support/solutions/folders/19000163093/page/1?url_locale=](https://help.hippovideo.io/support/solutions/folders/19000163093/page/1?url_locale=)

- Join our Slack channel for more updates/queries:
    
    [Slack](https://join.slack.com/t/hippo-video-sdk/shared_invite/zt-zz7v0uua-YqeLrgxWqyQfj0Kf61Z1Ig)
