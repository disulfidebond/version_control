# Version Control and Git
This writeup and brief tutorial wil lteach the basics of version control using Git. For in-depth instruction on Git commands, see [this writeup](https://git-scm.com/book/en/v1/Getting-Started-Git-Basics), or attend [Software Carpentry](https://uw-madison-datascience.github.io/git-novice-custom/)

## Preliminaries

1) Install Git
  * MacOSX: [See here](https://gist.github.com/disulfidebond/2dca7108eac56dd2c8bca6578d905cfd#check-to-see-if-xcode-commandline-tools-are-installed)
  * Ubuntu Linux: Open Terminal, and run these commands
  
          sudo apt-get update
          sudo apt-get install git

  * Windows: [See here](https://git-scm.com/download/win)

2) Check to see if git is installed:
  * On MacOSX and Linux, open a terminal and type *git*
  * On Windows, open Powershell and type *git*

## Basics
[Version Control](https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control) is a way to keep track of changes in a file over time and as edits or modifications are made to it. There are numerous version control systems (VCS) available. Git and svn are the most popular but by no means the only ones.

Here's a concrete example. Let's say there are two researchers, Jack and Jill, who are both working on a project. The project involves writing code and creating figures for presentation. The tasks for the project have been split between Jack and Jill, and both will be working on code and the figures at different points in time over the course of the project. To start, Jill creates a simple program in R, and creates a Github Gist with it:

        library(MASS)
        print('Hello World')
        df <- import.csv('data_for_figure.csv')
        df
        
Meanwhile, Jack starts on Figure 1 by downloading data from a website, and also creates a [Github Gist](https://gist.github.com/disulfidebond/6ff470c16e293bbc46582a63af2bc457):

        library(XML)
        library(RCurl)
        fileURL <- "https://open-ic.epic.com/FHIR/api/FHIR/DSTU2/Condition?patient=Tbt3KuCY0B5PSrJvCu2j-PlK.aiHsu2xUjUM8bWpetXoB"
        xData <- getUTL(fileURL)
        doc <- xmlParse(xData)

Jill navigates to the Github Gist, and tries the R code, but he finds a typo, and sends and email to Jack notifying her of the change. Both Jack and Jill can now see the [revisions history](https://gist.github.com/disulfidebond/6ff470c16e293bbc46582a63af2bc457/revisions).

Since only the creator can modify the Github Gist, Jill suggests that they create a Github repository so that both of them can edit the code. Jill does this, and creates [a public github repository with a README and the R code](https://github.com/disulfidebond/data_analysis/tree/version1). This repository has 2 branches: *Master*, which is the default branch and is always created when a new repository is made, and *version 1*, which Jill created as the development version of the current project.

Jack looks it over by creating a [fork](https://help.github.com/en/github/getting-started-with-github/fork-a-repo) of the *version 1* branch of the github repository.  He suggests adding the comments to the README wouldbe a better idea, so he makes this modification within Github and creates a *pull request*. A *pull request* must be approved by the owner (or someone with permission), and basically requests that the changes be merged back to the working version of the repository, which in this case is the version 1 fork.

Jill looks over the pull request, and approves it, thereby merging the two branches (or versions) into the current working development version of the repository. 
