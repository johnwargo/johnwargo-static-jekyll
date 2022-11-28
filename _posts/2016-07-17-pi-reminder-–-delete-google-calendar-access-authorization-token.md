---
layout: post
title:  Pi Reminder – Delete Google Calendar Access Authorization Token
date:   2016-07-17 20:16:00
categories: Internet of Things (IoT)
---
Note: This article refers to an older version of the Pi Remind application. In a subsequent update to the Google libraries, Google now places its configuration file in the same folder where the application executes. Refer to the [project's readme](https://github.com/johnwargo/pi-remind-hd#changing-the-google-profile) for additional information.

I’m in the process of changing jobs, so after I left my previous employer’s employment, I needed to reconfigure the Pi Reminder app to point it to my personal calendar profile instead of my work profile. If you remember the process, when you execute the Pi Reminder code on the Raspberry for the first time, it walks you through a process of authorizing the app to access your calendar (shown in Figure 1).

![Google Calendar Authorization Page](images/stories/2016/pi-remind-delete-auth-00.png)

Figure 1 – Authorizing Pi Reminder to Access a Google Calendar

When you complete this process, the Google Calendar API creates a hidden file on the Pi that contains the access token generated as part of this process. When it’s time to switch the Pi Reminder to use a new profile, all you have to do is delete that file.

Note: Before you can continue, you’ll need to stop the pi\_reminder.py process as it’s using the file we need to remove. If you ran the application manually in a terminal window, just terminate the process by closing the terminal window. If you’re like me and you used the desktop file I included in the project, then you’ll need to delete the file in the ~/.config/autostart folder. You can delete it then reboot the Pi before continuing with the remaining steps. Once we’re done, restore the file from the trash, reboot and you’ll be all set.

In my experience, Python code doesn’t like running as the Pi user, so in my instructions for starting the Pi Reminder code, I had you execute the code using the Linux sudo command. A side-effect of that is that the Google Calendar access token file is created by the root user and is not visible to normal users like the pi user. So, to whack the file (‘whack’ is a technical term for ‘delete’) you’ll need to do it with elevated privileges.

Note: There’s probably a lot of different ways you can do this, but I’m not a Linux expert, so I’m just going to show you how I did it. If you have a better way, that’s great, I don’t necessarily need to hear about it since this approach worked quite well for me.

Start by opening a terminal window. Once there, execute the following command:

`sudo pcmanfm`

The terminal will display the output shown in Figure 2 then open the Raspbian file manager application (shown in Figure 3), PCManFM.

![Raspbian terminal window](images/stories/2016/pi-remind-delete-auth-01.png)

Figure 2 – Raspbian Terminal Application

In the file manager, navigate to the file system’s /root folder as shown in the figure then double-click the .credentials folder to open it.

![Raspbian file manger window](images/stories/2016/pi-remind-delete-auth-02.png)

Figure 3 – Raspbian File Manager

Inside the folder is a file called pi\_remind.json (shown in Figure 4), that’s the file we’re looking for. Delete the file then close the file manager.

![Raspbian file manager window](images/stories/2016/pi-remind-delete-auth-03.png)

Figure 4 – Google API Access Token File

Next you’ll need to authorize Pi Reminder to use a different account with Google Calendar. Follow the instructions included with the original article to complete that step.