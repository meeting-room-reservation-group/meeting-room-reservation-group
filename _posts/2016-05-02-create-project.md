---
layout: post
title: Create a New Java Project
---

Start the new project with the Maven Archetype (template) for creating a Jersey RESTful API Service.


__Background__

Maven Archetypes for [Jersey](https://jersey.java.net/documentation/latest/getting-started.html#new-from-archetype) projects


## Action Plan

### Create Project Structure

Use the Maven Archetype with group-id `org.glassfish.jersey.archetypes` and artifact-id `jersey-quickstart-webapp` for creation
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

For those not using Eclipse the same thing can be done from the command-line, using the [Maven Archetype Plugin](http://maven.apache.org/archetype/maven-archetype-plugin/). This plug-in has the goal [archetype:generate](http://maven.apache.org/archetype/maven-archetype-plugin/generate-mojo.html) which creates a new Maven project, based on the Archetype.

Go to the directory `git`

	cd $HOME/git
	
Use Maven to generate to create the project structure 

    mvn  archetype:generate  -DgroupId=com.github.john.meeting-room-reservation  -DartifactId=meeting-room-reservation-services \
        -DarchetypeGroupId=org.glassfish.jersey.archetypes  -DarchetypeArtifactId=jersey-quickstart-webapp    -DarchetypeVersion=2.23 \
        -DinteractiveMode=false \
        -DarchetypeCatalog=https://repo1.maven.org/maven2/archetype-catalog.xml

This project can now be imported into Eclipse as an existing Maven project.


### Verify the Project

The project created through the Maven Archetype `jersey-quickstart-webapp` should now look similar as seen in the screenshot. Make sure the Eclipse Perspective _Java EE_ is active.   
[![Eclipse New Project Wizard]({{ site.url }}/images/eclipse/eclipse-new-maven-project-jersey-quickstart-webapp-00-s.jpeg)]({{ site.url }}/images/eclipse/eclipse-new-maven-project-jersey-quickstart-webapp-00.jpeg)

- The Markers window shows one _JSP Problem_, to fix this add the Maven dependency `javax.servlet-api`
- Open the file `pom.xml` and add the required dependency  
{% highlight xml %}
    <dependency>
        <groupId>javax.servlet</groupId>
        <artifactId>javax.servlet-api</artifactId>
        <version>3.1.0</version>
    </dependency>
{% endhighlight %}

- Save the modification, this will trigger Eclipse to check the Maven dependencies and when changed, rebuild the project again. This will remove the error from the _Markers_ window.

__Run the Web Application Project__

__INFO__ Make sure the [Eclipse Jetty feature](http://verhagen.github.io/eclipse-tip-marketplace-add-jetty/) is installed.

- Go to the window _Project Explorer_ and on the project (here _meeting-room-reservation-services_) use the context menu: _Run As > Run with Jetty_
![Eclipse New Project Wizard]({{ site.url }}/images/eclipse/eclipse-run-as-run-with-jetty-00.jpeg)
- This will launch Jetty as seen in the console
  __WARNING__ Make sure you see the red line ending with: _SelectChannelConnector@0.0.0.0:8080_ This indicates that Jetty has successfully started.  
[![Eclipse New Project Wizard]({{ site.url }}/images/eclipse/eclipse-run-as-run-with-jetty-01-tn.jpeg)]({{ site.url }}/images/eclipse/eclipse-run-as-run-with-jetty-01.jpeg)

__Verify the Web Application with a (Graphical) Web Browser__

- Open a browser (Chrome, Firefox, Opera, Safari, or other) and go to [http://localhost:8080](http://localhost:8080) this should show the page as seen below (this is actually the `index.jsp` of the project)  
![Eclipse New Project Wizard]({{ site.url }}/images/eclipse/eclipse-run-as-run-with-jetty-02.jpeg)
- Check if the Web Application _Resource_ exists [http://localhost:8080/webapi/myresource](http://localhost:8080/webapi/myresource)  
![Eclipse New Project Wizard]({{ site.url }}/images/eclipse/eclipse-run-as-run-with-jetty-03.jpeg)


__Verify the Web Application with a (Text) Web Browser__

Use [curl](https://curl.haxx.se/) to see the same content, but just in plain text. Use the option `-v` to also see all the request / replay details.

- Open a command terminal and enter the curl command `curl  localhost:8080`  
  This should show the content of the html page
![Eclipse New Project Wizard]({{ site.url }}/images/eclipse/eclipse-run-as-run-with-jetty-04.jpeg)

- Use curl to get the content of the resource `curl  localhost:8080/webapi/myresource`  
  This should show the content of the resource (just the text `Got it!`)  
![Eclipse New Project Wizard]({{ site.url }}/images/eclipse/eclipse-run-as-run-with-jetty-04b.jpeg)
- Use curl to get the content of the resource in _verbose_ mode `curl  -v  localhost:8080/webapi/myresource`. This will show the request and response headers as well.  
![Eclipse New Project Wizard]({{ site.url }}/images/eclipse/eclipse-run-as-run-with-jetty-04c.jpeg)


## Jetty Commands

In the Jetty console, you can enter commands like:

- help - Shows the available commands
- stop - Stops Jetty (or use the small red stop rectangle, from the speed button bar menu)
- restart - reloads the Web Application(s) that are deployed in this Jetty instance

[![Eclipse New Project Wizard]({{ site.url }}/images/eclipse/eclipse-run-as-run-with-jetty-05-tn.jpeg)]({{ site.url }}/images/eclipse/eclipse-run-as-run-with-jetty-05.jpeg)
