---
layout: post
title: Create Local Git Repository
---
Adding a (new) project to a new local git repository. 


## Action Plan

### Add Git Ignore File

There are many files, which should not be added to the git project repository, because they are configuration files for Eclipse, IntelliJ or output files from the Maven build, or other processes. Only those files that are can not be generated, should end up in a source repository.

Eclipse and IntelliJ can read Maven configuration files `pom.xml` to create their own specific configuration files.

Create the [git ignore](http://verhagen.github.io/git-tip-ignore-files/) file. 


### Add README

Every project should have a `README.md` which explains the general idea of the project, high level overview, links to important parts.

__TIP__ The file is written in [MarkDown](https://guides.github.com/features/mastering-markdown/) format. A simple text format with easy formatting rules.

__Sample README.md__

{% highlight markdown %}
# Project Title

This project ...
{% endhighlight %} 


### Create Local Git Repository

- TODO


### Add and Commit the Project Files to the Local Git Repository

- TODO
