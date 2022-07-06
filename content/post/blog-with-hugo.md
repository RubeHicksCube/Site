---
title: "Blog With Hugo"
date: 2022-07-05T10:04:29-06:00
draft: false
---

The main issue I have with static site generators is that they need to push their own content using scripts that, for condign newbie, are hard to understand.

The benefits of WordPress are that you can have the "new post" page bookmarked and with a single click you can have a new post going.

With hugo, you have to remember a command, ableit a simple one, to make a new document, and then push it to make an html file.

The problem with this is that I have to install Hugo and whatever other scripting service on whichever computer I want to work from.

The best solution to this is to have a server at home with everything installed that I can remote into. But now I eliminated the main benefit of a static site which is off-network writing.

This isn't a huge issue as I can write on any text editor and paste it in later. But, it just takes an extra step. 

So, below are step by steps to get up and running with Hugo without all the confusion that even their official site has.

----

First is to download [Chocolatey](https://gohugo.io/getting-started/installing/#chocolatey-windows), a package isntaller.

Then, [On Windows](https://gohugo.io/getting-started/installing/#windows), go to your Documents folder, make a /Hugo/ folder and inside that make a /bin/ folder.
And also have the [Package](https://github.com/gohugoio/hugo/releases) downloaded, and extract its contents into the /bin/.

>There's an added step with windows to go into the environment variables to edit those settings.

>Hit the start button, and type in "environment" and hit enter.

>In the "Advanced" tab, hit the "Environemtn Variables" button.

>Select "Path" Variable. Then "Edit" button.

>Select an open bar and click "New", "Browse" and then navigate to the /bin/ folder made before.

>Hit "Ok" as many time to close out the window.

----

