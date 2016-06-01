---
layout: post
title: Create a New Java Project
---

Start the new project with the Maven Archetype (template) for creating a Jersey RESTful API Service.


__Background__

Maven Archetypes for [Jersey](https://jersey.java.net/documentation/latest/getting-started.html#new-from-archetype) projects


## Action Plan

### Create Project Structure

Use the Maven Archetype with group-id `org.glassfish.jersey.archetype` and artifact-id `jersey-quickstart-webapp` for creation
of the initial project structure.

__Using Eclipse__

- Use Eclipse menu: _File > New > Project..._
- The dialog _New Wizard_ will open  
- Select from the tree _Maven > Maven Project_
![Eclipse New Project Wizard]({{ site.url }}/images/eclipse/eclipse-new-project-maven-project-00.jpeg)
- Use button __Next__ to continue
- Remove the check box _Use default Workspace location_
- Enter the _Location_ where the (git) project should be created  
  In this example there is the user john, who has a git directory, in which he places all his (git) projects. The name of this new project is `meeting-room-reservation-services`  
![Eclipse New Project Wizard]({{ site.url }}/images/eclipse/eclipse-new-project-maven-project-01.jpeg)
- Use button __Next__ to continue
- Enter in the field _Filter_ the text __jersey-quickstart-webapp__  
  After several seconds there should appear two entries  
![Eclipse New Project Wizard]({{ site.url }}/images/eclipse/eclipse-new-project-maven-project-02.jpeg)
- Choose the 2nd edition (here version __2.23__)  
  Details about the Archetype are shown in the description window  
![Eclipse New Project Wizard]({{ site.url }}/images/eclipse/eclipse-new-project-maven-project-03.jpeg)
- Use button __Next__ to continue
- The dialog will show _New Maven Wizard - Specify Archetype parameters_
- Enter as _Group Id_ the unique reverse url, of your github account  
  Here we combine John his account on github to: `com.github.john` and add the project name to it `meeting-room-reservation`  
  Create your own unique groud-id similar to `com.github.<account>.meeting-room-reservation`
- Enter as _Artifact Id_ text `meeting-room-reservation-services`  
  __TIP__ Keep this the same as the (git) project name, for easy association
  __WARNING__ Group id and artifact id should be inline with Maven naming conventions, all lower-case letters, words separated with dashes.
- Enter the (Java) _Package_ name `com.github.<account>.mrrs`  
  __INFO__ Here we create an abbreviation `mrrs`, because otherwise the package name get very long.  
![Eclipse New Project Wizard]({{ site.url }}/images/eclipse/eclipse-new-project-maven-project-04.jpeg)
- Use button __Finish__ so the project structure is created, for this Maven Archetype

__TIP__: In case the Maven Archetype is not found, [add the Maven Archetypes Catalog](http://verhagen.github.io/eclipse-tip-add-maven-archetypes-catalog/) `https://repo1.maven.org/maven2/archetype-catalog.xml` in Eclipse.


__Using Maven Command Line__

TODO

### Verify the Project

The project created through the Maven Archetype `jersey-quickstart-webapp` should now look similar as seen in the screenshot. Make sure the Eclipse Perspective _Java EE_ is active.   
![Eclipse New Project Wizard]({{ site.url }}/images/eclipse/eclipse-new-maven-project-jersey-quickstart-webapp-00.jpeg)

__INFO__ Make sure the [Eclipse Jetty feature](http://verhagen.github.io/eclipse-tip-marketplace-add-jetty/) is installed.

- The Markers window shows one _JSP Problem_, to fix this add the Maven dependency `javax.servlet-api`
- Open the file `pom.xml` and add the required dependency

	<dependency>
		<groupId>javax.servlet</groupId>
		<artifactId>javax.servlet-api</artifactId>
		<version>3.1.0</version>
	</dependency>
