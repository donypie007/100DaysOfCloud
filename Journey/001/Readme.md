# Day 1 - Preparing the Environment - Visual Studio Code and Gituhub Source Control

## Introduction

I’ve always believed that good preparation is the key to success, and Day 1 is going to be about setting up the environment for use.

I’ve decided to split my 100 days across 3 disciplines:

-	Azure, because it’s what I know
-	AWS, because its what I want to know more about
-	And the rest of it …. This could mean anything: GitOps, CI/CD, Python, Ansible, Terraform, and maybe even a bit of Google Cloud thrown in for good measure.

It’s not exactly going to be an exact 3-way split across the disciplines, but let’s see how it goes.
Let’s start the prep. The goal of the 100 Days for me is to try and show how things can be done/created/deleted/modified etc. using both GUI and Command Line. For the former, we’ll be going what it says on the tin and clicking around the screen. For the latter, it’s going to be done in Visual Studio Code.

![image](https://user-images.githubusercontent.com/80047500/133880895-b32e9f4a-af9d-4288-b30a-ed905285d48a.png)

## Prerequisite

Need a Windows Desktop (Can be Laptop, PC or Virtual Machine) in order ot install Visual Studio Code

## Instructions

To download, we go to https://code.visualstudio.com/download , and choose to download the System Installer:
 
![image](https://user-images.githubusercontent.com/80047500/133880910-66c4570e-5913-427a-b396-a3a70c39677a.png)

Once the download completes, run the installer (Select all options). Once it completes, launch Visual Studio Code:

![image](https://user-images.githubusercontent.com/80047500/133880914-63199111-15dc-4fbb-9925-840042318c8c.png)
 
After selecting what colour theme you want, the first place to go is click on the Source Control button. This is important, we’re going to use Source Control to manage and track any changes we make, while also storing our code centrally in GitHub. You’ll need a GitHub account (or if you’re using Azure GitOps or AWS Code Commit, you can use this instead). For the duration of the 100 Days, I’ll be using GitHub. Once your account is created, you can create a new repository (I’m calling mine 100DaysRepo)

![image](https://user-images.githubusercontent.com/80047500/133880920-0b229d4d-bbe0-427d-9099-885a971e1c29.png)
 
So now, let’s click on the “install git” option. This will redirect us to https://git-scm.com, where we can download the Git installer. When running the setup, we can do defaults for everything EXCEPT this screen, where we say we want Git to use Visual Studio Code as its default editor:

![image](https://user-images.githubusercontent.com/80047500/133880929-996f2f40-b578-45b0-ba16-ccba0ca173ca.png)
 
Once the Git install is complete, close and re-open Visual Studio Code. Now, we see we have the option to “Open Folder” or “Clone Repository”. Click the latter option, at the top of the screen we are prompted to provide the URL of the GitHub Repository we just created. Enter the URL, and click “Clone from GitHub”:

![image](https://user-images.githubusercontent.com/80047500/133881016-337bfc68-76b9-45ae-af7a-01fa923481f0.png)
 
We get a prompt to say the extension wants to sign into GitHub – click “Allow”:

![image](https://user-images.githubusercontent.com/80047500/133881022-d4480df8-336c-4a7e-9369-f097bfce4e4b.png)
 
Clicking “Allow” redirects us to this page, click “Continue”:

![image](https://user-images.githubusercontent.com/80047500/133881027-7870e1f2-91e2-4117-91e6-45fb92816b27.png)
 
This brings us to the logon prompt for GitHub:

![image](https://user-images.githubusercontent.com/80047500/133881029-9343dcd0-cac1-4a9e-9826-6cfffe5a979b.png)
 
This brings up “Success” message and an Auth Token: 

![image](https://user-images.githubusercontent.com/80047500/133881037-0fc5af17-bf39-4dff-bd97-9aff8e5d8daf.png)

Click on the “Signing in to github.com” message at the bottom of the screen, and then Paste the token from the screen above into the “Uri” at the top:

![image](https://user-images.githubusercontent.com/80047500/133881092-f171f7b9-94b4-4791-910e-63d1660ed7c4.png)
 
Once this is done, you will be prompted to select the local location to clone the Repository to. Once this has completed, click “Open Folder” and browse to the local location of the repository to open the repository in Visual Studio Code.

![image](https://user-images.githubusercontent.com/80047500/133881099-3c32d07b-55f6-4618-b0de-987986b03d2f.png)
 
Now, let’s create a new file. It can be anything, we just want to test the commit and make sure it’s working. So let’s click on “File-New File”. Put some text in (it can be anything) and then save the file with whatever name you choose:

![image](https://user-images.githubusercontent.com/80047500/133881100-04673ee5-be4a-490a-b065-a6b783528860.png)
 
My file is now saved. And we can see that we now have an alert over in Source Control:

![image](https://user-images.githubusercontent.com/80047500/133881107-cc3c6756-f9b8-46ce-82e9-63678ba333f7.png)
 
When we go to Source Control, we see the file is under “Changes”. Right-click on the file for options:

![image](https://user-images.githubusercontent.com/80047500/133881112-4eea74c5-df5a-4d16-aff1-a7f78c434ce7.png)
 
We can choose to do the following:
-	Discard Changes – reverts to previous saved state
-	Stage Changes – saves a copy in preparation for commit
When we click “Stage Changes”, we can see the file moves from “Changes” to “Staged Changes”. If we click on the file, we can see the editor brings up the file in both states – before and after changes:

![image](https://user-images.githubusercontent.com/80047500/133881158-f8127a86-ee0a-4c94-8e05-06669e76eb93.png)
 
From here, click on the menu option (3 dots), and click “Commit”. We can also use the tick mark () to Commit:

![image](https://user-images.githubusercontent.com/80047500/133881162-9655a82b-29d3-406a-9da0-d8266666ee7e.png)
 
This then prompts to provide a commit message. Enter something relevant to the changes you’ve made here and hit enter:

![image](https://user-images.githubusercontent.com/80047500/133881167-e72b55f0-584f-46c8-b0c8-2260082de939.png)
 
And it fails!!!

![image](https://user-images.githubusercontent.com/80047500/133881172-40919b12-f3a6-4548-b83c-7c41b65e239e.png)
 
OK, so we need to configure a Name and Email ID in GitBash. So open GitBash and run the following:
git config --global user.name "your_name"
git config --global user.email "your_email_id"

![image](https://user-images.githubusercontent.com/80047500/133881177-4d398742-4861-43d2-aeca-f74fb03073e9.png)
 
So let’s try that again. We’ll commit first:

![image](https://user-images.githubusercontent.com/80047500/133881241-2a6e450c-01aa-47e2-a027-c4bde2cd8655.png)
 
Looks better, so now we’ll do a Push:

![image](https://user-images.githubusercontent.com/80047500/133881248-d794fb9a-148f-4cb9-b78e-72e6dea00d5c.png)
 
And check to see if our file is in VS Code? Yes it is!

![image](https://user-images.githubusercontent.com/80047500/133881256-f9f944a8-f38b-4584-bfb4-075704de4d2f.png)

## Next Steps

OK, so that’s our Repository done and Source Control and cloning with GitHub configured. 
That’s the end of Day 1! As we progress along the journey and as we need them, I’ll add some Visual Studio Code extensions which will give us invaluable help along the journey. You can browse these by clicking on the “Extensions” button on the right:

![image](https://user-images.githubusercontent.com/80047500/133881259-59e07f2c-ece7-4449-a6ee-17f48ffa4d9f.png)
 
Extensions add languages, tools and debuggers to VS Code which auto-recognize file types and code to enhance the experience. Until next time!


## Social Proof

[Medium](https://durkanm.medium.com/100-days-of-cloud-day-1-preparing-the-environment-29c16ac3dc8)

[LinkedIn](https://www.linkedin.com/posts/michael-durkan-1a72a759_100-days-of-cloudday-1-preparing-the-activity-6844395875175809024-AyTh)

[Twitter](https://twitter.com/durkanm/status/1438628880143761409)


