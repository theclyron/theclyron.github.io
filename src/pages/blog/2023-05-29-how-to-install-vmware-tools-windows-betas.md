---
layout: "../../layouts/BlogPostLayout.astro"
title: "How to install VMware Tools on Windows Betas"
desc:
date: 29 May 2023
---
A tutorial on how to install VMware Tools on a Windows beta build. Yes, it may be theoretically as "simple" to install as on VMs with stable/non-beta Windows releases, but the timebomb is what makes things difficult. I've already made this guide in video-form in late 2022 ([click/tap here to watch][1]), but haven't thought of writing a text-form version of the guide until now, so here it is!

## Step 1: Edit the .VMX file
In order for the guest time to not sync with the host time, and thus trigger the timebomb, we'll have to edit the .VMX file of the VM with the installation of the Windows beta where you wish to install VMware Tools on.

To get to the .VMX file, you have to navigate to the directory where the VM is on (alternatively, if you use Workstation Pro, you can right click on the VM and then click on "Open VM directory" in the context menu). Open the .VMX file in your preferred text editor.

Make sure all these lines are added into the .VMX file:

```
time.synchronize.continue = "FALSE"
time.synchronize.restore = "FALSE"
time.synchronize.resume.disk = "FALSE"
time.synchronize.shrink = "FALSE"
time.synchronize.tools.startup = "FALSE"
```
<br>
Afterwards, save the .VMX file.

## Step 2: Install VMware Tools
Before proceeding in, please make sure "Synchronize guest time with host" is unchecked in Virtual Machine Settings, at the VMware Tools settings in the Options tab.

Afterwards, turn on the VM, then install VMware Tools like you would do on stable/non-beta Windows releases *without worry*. Below I'll link to .ISO images for VMware Tools 10.2.1 and VMware Tools 9, use the one that works best in the beta build.

* VMware Tools 10.2.1 - [download on Google Drive][2]
* VMware Tools 9 - [download on Google Drive][3]

Though, if you're installing VMware Tools on a VM running some Windows 10/11 build, then simply installing it through "VM -> Install VMware Tools" (or "Manage -> Install VMware Tools", in the case of VMware Player) should definitely work too.

[1]: https://youtu.be/-KFsqaB86iw
[2]: https://drive.google.com/file/d/1ztLZ-K_q8bDqw2Bvj26TV9XytE8qbKVo/view?usp=sharing
[3]: https://drive.google.com/file/d/1jZASKmCQ93sWf3Vr07KEt87ffCE1BP0t/view?usp=sharing