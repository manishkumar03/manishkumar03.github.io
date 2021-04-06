---
layout: post
title: "How to make Nikon Capture NX2 run faster."
date: "2009-02-25"
tags: 
  - "photography"
  - "software"
---

To say that Nikon Capture NX (or Capture Nx2) is slow would be an understatement. The reason for its slowness is that it ships with older versions of certain Windows files which it uses. So all we need to do to make it run faster is to install the latest and greatest versions of these files. It really is that simple and it makes a significant difference. But why Nikon doesn't document it or doesn't do it by default is beyond me.

Here are the steps (Please read the whole post before proceeding with the install):

1\. Download and install Microsoft .NET Framework 3.5 with Service Pack 1 from [this page](http://www.microsoft.com/downloads/details.aspx?familyid=ab99342f-5d1a-413d-8319-81da479ab0d7&displaylang=en) on Microsoft's site. Capture NX2 installer specifies that it needs .NET framework 2.0 but if you install .NET framework 3.5, you do not need .NET Framework 2.0 or any other earlier version.

Note: If you do not want to install .NET Framework 3.5 for any reason and want to use version 2.0 itself, download the latest version of 2.0 with SP1 from [this page](http://www.microsoft.com/downloads/details.aspx?FamilyID=79bc3b77-e02c-4ad3-aacf-a7633f706ba5&displaylang=en).

Install updates, if any, through Windows Update (in Internet Explorer). If you already have .NET framework installed (2.0 or later), use Windows Update to get the latest version. Reboot if prompted.

2\. Download and install Microsoft Visual C++ 2008 SP1 Redistributable Package from [this page](http://www.microsoft.com/downloads/details.aspx?familyid=A5C84275-3B97-4AB7-A40D-3802B2AF5FC2&displaylang=en) on Microsoft's site. It's a very small download (only 4 MB). If you install this, you do not need Microsoft Visual C++ 2005 Redistributable Package or any other earlier version. Capture NX2 ships with a very old version of this file (from 2005 or earlier) which is the main reason it runs slow.

3\. Reboot your computer.

4\. Install Nikon Capture NX (or NX2). If you have already installed it, you do not have to install it again. But if you are doing a fresh install, it's better if you install it in the end.

5\. Enjoy editing.
