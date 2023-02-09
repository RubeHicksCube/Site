---
title: "Blog With Hugo"
date: 2022-07-05T10:04:29-06:00
draft: false
summary: "Hugo is complicated! Here's some tips!"
---

The main issue I have with static site generators is that they need to push their own content using scripts that, for condign newbie, are hard to understand.

The benefits of WordPress are that you can have the "new post" page bookmarked and with a single click you can have a new post going.

With hugo, you have to remember a command, ableit a simple one, to make a new document, and then push it to make an html file.

The problem with this is that I have to install Hugo and whatever other scripting service on whichever computer I want to work from.

The best solution to this is to have a server at home with everything installed that I can remote into. But now I eliminated the main benefit of a static site which is off-network writing.

This isn't a huge issue as I can write on any text editor and paste it in later. But, it just takes an extra step. 

So, below are step by steps to get up and running with Hugo without all the confusion that even their official site has.

----

- First is to download [Chocolatey](https://gohugo.io/getting-started/installing/#chocolatey-windows), a package installer.

>Run this command in PowerShell as administrator and it will install.
>Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))

- Then, [On Windows](https://gohugo.io/getting-started/installing/#windows), go to your Documents folder, make a /Hugo/ folder and inside that make a /bin/ folder.
- Ensure you have [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) Installed.
- Ensure you have [Go](https://go.dev/doc/install) Installed.
- Ensure you have [Visual Studio Code](https://code.visualstudio.com/Download) Installed.
- Ensure you have [GitHub Desktop](https://desktop.github.com/) Installed.

>There's an added step with windows that may have to be performed to ensure everything works properly. If your installation automattically does this step, then disregard this step. Go into the environment variables and ensure a path to your installation is mapped:

>Hit the start button, and type in "environment" and hit enter.

>In the "Advanced" tab, hit the "Environment Variables" button.

>Select "PATH" Variable. Then "Edit" button.

>Select an open bar and click "New", "Browse" and then navigate to the /bin/ folder made before.

>Hit "Ok" as many time to close out the window.

----

## How to use Hugo

When you have everything installed, you will write posts for your blog using a .md (markdown) file. You can draft these directly in Visual Studio, or, use a program like Obsidian. Whatever you draft will be dropped in the "post" folder in Hugo.

Make your post, and then in the terminal from Visual Studio you'll type "Hugo" to have it process the file into an HTML file format that is readable by your browser.

That's it! Use GitHub Desktop to push the build to GitHub, and then Netlify or GitHub Pages to share with the world!