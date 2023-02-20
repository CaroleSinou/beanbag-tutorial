# How to publish the Bean Bag online

This tutorial has been created by *Carole Sinou* and *Charlotte Hagelstam Renshaw*.
It is intended to provide information on how to transform the content of the PDF version of the Bean Bag to the online version.


## How to access files and folders

All files for the Legume Data Portal are available on the GBIF GitHub hp-legume repository (<https://github.com/gbif/hp-legume>).
If you need admin rights, please contact [Carole Sinou](mailto:canadensys.networl@gmail.com).
You can use a desktop application, like [GitHub Desktop](https://desktop.github.com/) or directly work within GitHub.

## How to create the skeleton of the online Bean Bag

1. In the folder "\_data", open the file "sidenav" (both in the main "\_data" folder and in the "fr" folder within "\_data"). At the top of each file (en and fr versions), you need to add the information for each section. See examples from [older issues of Bean Bag](https://github.com/gbif/hp-legume/blob/master/_data/sidenav.yml). 
This information will be displayed in the left panel of each BB page on the portal (side navigation).

![](/image/Sidenav-example.png)


2. In the folder "beanbag", create a folder for the new issue, based on the number of the issue (ex. 69).  
Within that folder, create a file called XXcontent.md (replacing XX by the issue number).  
This file create the ‘Content’ page for that issue (<https://www.legumedata.org/beanbag/69/69content/>).

	![](/images/contentPage.png)

	This page is the equivalent to the Table of Content in the PDF version.  
	You can open the XXcontent.md file available for older issues to understand how it is constructed.  
	The first part of the file (at the top of the file) is called "Front Matter" and allows to specify parameters.

	Ex.:   
	\---  
	layout: post  
	lang-ref: /beanbag/69content  
	title: Issue 69, Year 2022  
	background: /assets/images/69/welcome_mimosa.jpg  
	description: Content of the issue 69 (2022)  
	height: 70vh  
	---\  

	- Layout specifies the type of layout used for the page
	- lang-ref gives access to the page in the selected language. Note: we do not translate BB content, and we do not create a French version of each file
	- title is the title displayed on the page
	- background is used to specify the image used in background
	- description is a short description displayed after the title
	- height specifies the size of the image (the part that will be displayed)

	After the front matter, you will be able to copy-paste the text from the Table of Content of the PDF version of the Bean Bag, and you will need to format it.  
	You can find more information about mardown basic syntax [here](https://www.markdownguide.org/basic-syntax/).

	To include images within the page, you can use [markdown syntax](https://www.markdownguide.org/basic-syntax/#images-1) or html (when you want the image to be embended within the text, like in this page: <https://www.legumedata.org/beanbag/69/issue-69-rupert-barneby-award>)  


3. In folder /assets/images/, create a folder corresponding to the volume number.  
All images you want to include in the Bean Bag needs to be place in this folder.

4. In folder /media/, add the PDF version of the Bean Bag. Please try to use the same name formatting as the older versions.

5. In "\_data", open the file "beanbag.md" (also the same file within "\_data/fr/").  
Just after the line starting by "features", add these information:

	\- preTitle: Year XXXX  # corresponding year of the volume  
	      title: Issue XX # XX is the number of the volume  
	      background: /assets/images/XX/Name_of_the_image_on_the_cover.jpg  
	      href: /beanbag/XX/XXcontent # replace XX by the number of the volume  
	      cta:  
	      - text: Download  
	        href: /media/The_BB_Newsletter_IssueXX_20XX.pdf # file name of the PDF version of the BB, located in the "media" folder  
	        isPrimary: true  
	      - text: Read  
	        href: /beanbag/XX/XXcontent # link to the content page for the XX volume  
	        isPrimary: true  

![](/images/BeanBag-Issue-page.png)

6. Create a news item announcing the new issue.  
If you are not comfortable doing it yourself, contact [Carole Sinou](mailto:canadensys.networl@gmail.com)  

## How to add all articles and reports available in the PDF version

For each article in the Bean Bag, create a file with the name formatted like this: issue-XX-name-of-the-article.md  
For each file, you will need to add the front matter and the text.

Front Matter:  
\---  
layout: documentation  
lang-ref: beanbag/69/issue-69-8ILC  
permalink: /beanbag/69/issue-69-8ILC  
title: 8th International Legume Conference (8ILC)  
description: Issue 69 - 8th International Legume Conference (8ILC)  
sideNavigation: sidenav.beanbag69  
---\

- The layout for all Bean Bag articles is "documentation"
- lang-ref: links to the file in the right language (we do not have a French version of the Bean Bag)
- permalink is the permanent link to the file, here the direct path to the file
- title: Title of the page
- description: short description of the page
- sideNavigation: link to the file displaying the side navigation

After the front matter, you just need to copy-paste the text and format it the same way you did for the content page.

![](/images/ExamplePageArticle.png)

## Push the content to the staging portal

Within GitHub or GitHub Desktop, push the changes you made, indicating what you have done.  
You can follow the state of the Staging Portal on the [JeKyll page provided by GBIF](https://builds.gbif.org/view/Hosted%20Portals/job/hp-legume/)  
Review all pages for the new volume and all pages regarding the Bean Bag to verify that everything is looking good.  
If you need to make changes, you will have to push again the corrected files and the staging portal will be rebuild.

## Release a new version of the production portal

On the GitHub page (https://github.com/gbif/hp-legume), click on "Release" appearing on the right-side of the page.  
Then click on "Draft a new release" at the top-right of the page.  

![](/images/New-release.png)

Click on "Choose a tag", and create a new tag with a new version. For example "v.1.3.12". If this release contains important modifications to the website, you can change the version to v.1.4.0, or even v.2.0.0  
Give an informative title and a description to the release.  
Click on "Publish release" and wait a little bit while the production portal is rebuilding. It will take several minutes.  
Check the [portal](https://www.legumedata.org/) to verify the new pages.  
