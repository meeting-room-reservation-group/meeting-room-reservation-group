---
layout: post
title: Add Cucumber Features
---
After thinking about the requirements, it time to create the Cucumber feature files.


## Action Plan

- Add Cucumber dependencies

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

- Create directories for the Cucumber feature files and Cucumber step classes

- Create directory for Cucumber step classes  
  `mkdir  src/it/java`
- Create directory for Cucumber feature file  
  `mkdir  src/it/resources`

- Add [Maven failsafe plug-in](http://maven.apache.org/surefire/maven-failsafe-plugin/)

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

- Install Cucumber for Eclipse feature  
  Use the Eclipse update site: `http://cucumber.github.com/cucumber-eclipse/update-site`


