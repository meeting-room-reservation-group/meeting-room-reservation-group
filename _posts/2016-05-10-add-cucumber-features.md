---
layout: post
title: Add Cucumber Features
---
After thinking about the [requirements]({% post_url 2016-05-04-requirements %}), it time to create the Cucumber feature files. And add them to the project.

To make it possible to run these [Specification by Example]()s,   


## Action Plan

- Add the required Cucumber dependencies.

{% highlight plain text %}
        <dependency>
            <groupId>info.cukes</groupId>
            <artifactId>cucumber-java</artifactId>
            <version>1.2.0</version>
            <scope>test</scope>
        </dependency>
        <dependency>
            <groupId>info.cukes</groupId>
            <artifactId>cucumber-junit</artifactId>
            <version>1.2.0</version>
            <scope>test</scope>
        </dependency>
{% endhighlight %}

- Create directories for the Cucumber feature files and Cucumber step classes.

- Create directory for Cucumber step classes  
  `mkdir  src/it/java`
- Create directory for Cucumber feature file  
  `mkdir  src/it/resources`

- Add the new directories as Eclipse source Folders  
  Select both directories `java` and `resources` and use the mouse menu: _Build Path > Use as Source Folder_ 

- Add [Maven failsafe plug-in](http://maven.apache.org/surefire/maven-failsafe-plugin/) to the Maven Project Configuration `pom.xml`

{% highlight plain text %}
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-failsafe-plugin</artifactId>
                <version>2.19.1</version>
                <executions>
                    <execution>
                        <goals>
                            <goal>integration-test</goal>
                            <goal>verify</goal>
                        </goals>
                    </execution>
                </executions>
            </plugin>
{% endhighlight %}


- Create a Java package with a name similar as the package name in `src/main/java`.  
  The top level package name for the project is `com.github.<github-user>.mrrs`.  
  Create a new package name in `src/it/java` for the integration tests `com.github.<github-user>.mrrs.it`
 
- Create a new class, in the package `com.github.<github-user>.mrrs.it`, that will run Cucumber feature files.
  Give this class a clear name like `RunCucumberTests`.

{% highlight java %}
import org.junit.runner.RunWith;

import cucumber.api.CucumberOptions;
import cucumber.api.junit.Cucumber;

@RunWith(Cucumber.class)
@CucumberOptions(
		plugin = { "html:target/cucumber/report.html", "json:target/cucumber-report.json" }, 
		features = { "src/it/resources/" })
public class RunCucumberTests {
	// No implementation required
}
{% endhighlight %}


## Install Cucumber for Eclipse feature

  Use the Eclipse update site: `http://cucumber.github.com/cucumber-eclipse/update-site`


## Create New Feature File

- Create the Cucumber feature file `room.feature`, in the directory `src/it/java` for the room features.

{% highlight plain text %}
Feature: Rooms require a location and capacity. Optional they have a name and facilities.


Scenario: Room can be found by location
Given a room with name "Berlin", location "1.12" and capacity 12 
	And which has facility "whiteboard"
When searching for room with location "1.12"
Then the room with name "Berlin" should be returned
{% endhighlight %}

- Create a new class `RoomSteps` place it in the package `com.github.<github-user>.mrrs.it.cucumber`.

{% highlight java %}
public class RoomSteps {

}
{% endhighlight %}

