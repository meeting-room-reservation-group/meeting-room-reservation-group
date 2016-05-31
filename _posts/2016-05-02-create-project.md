---
layout: post
title: Create a New Java Project
---

Start the new project with the Maven Archetype (template) for creating a Jersey RESTful API Service.


__Background__

Maven Archetypes for [Jersey](https://jersey.java.net/documentation/latest/getting-started.html#new-from-archetype) projects


# Action Plan

## Create Project Structure

Use the Maven Archetype with group-id `org.glassfish.jersey.archetype` and artifact-id `jersey-quickstart-webapp` for creation
of the initial project structure.

__Using Eclipse__

- Use Eclipse menu: _File > New > Project..._
- The dialog _New Wizard_ will open  
![Eclipse Preferences]({{ site.url }}/images/eclipse/eclipse-new-project-maven-project-00.jpg)
- Select from the tree on the left _Maven > Maven Project_
- Use button __Next__ to continue
- Remove the check box _Use default Workspace location_
- Enter the _Location_ where the git project should be created  
  In this example there is the user john, who has a git directory, in which he places all his  
  git projects. The name of his new git project is `meeting-room-reservation-services`  
![Eclipse Preferences]({{ site.url }}/images/eclipse/eclipse-new-project-maven-project-02.jpg)
- Use button __Next__ to continue
- Enter in the field _Filter_ the text __jersey-quickstart-webapp__  
  After several seconds there should appear two entries
- Choose the 2nd edition __2.23__  
  Details about the Archetype are shown in the description window
- Use button __Next__ to continue
- The dialog will show _New Maven Wizard - Specify Archetype parameters_
- Enter as _Group Id_ the unique reverse url, of your github account  
  Here John is account on github is: `com.github.john` and add the project name to it `meeting-room-reservation`  
  Create your own unique groud-id similar to `com.github.<account>.meeting-room-reservation`
- Enter as _Artifact Id_ text `meeting-room-reservation-services`  
  __TIP__ Keep this the same as the (git) project name, for easy association
  __WARNING__ Group id and artifact id should be inline with Maven naming conventions, all lower-case letters, words separated with dashes.
- Enter the (Java) _Package_ name `com.github.<account>.mrrs`  
  Here we create an abbreviation `mrrs`, because otherwise the package name get very long.


__TIP__: In case the Maven Archetype is not found, [add the Maven Archetypes Catalog](http://verhagen.github.io/eclipse-tip-add-maven-archetypes-catalog/) `https://repo1.maven.org/maven2/archetype-catalog.xml` in Eclipse.


__Using Maven command line__

TODO

## Verify the Project

- TODO


## Add Git Ignore File

There are many files, which should not be added to the git project repository, because they are configuration files for Eclipse, IntelliJ or output files from the Maven build, or other processes. Only those files that are can not be generated, should end up in a source repository.

Eclipse and IntelliJ can read Maven configuration files `pom.xml` to create their own specific configuration files.

Create the [git ignore](http://verhagen.github.io/git-tip-ignore-files/) file. 


## Create Local Git Repository

- TODO


## Add and Commit the Project Files to the Local Git Repository

- TODO
