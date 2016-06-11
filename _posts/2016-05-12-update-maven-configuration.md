---
layout: post
title: Update Maven Configuration
---
Through the Maven configuration file `pom.xml` the required dependencies as well as the used Maven plug-in are configured. During the
[Create a New Project]({% post_url 2016-05-02-create-project %}), the initial `pom.xml` is created. Now is a good time to check if everything
is up to date.


## Action Plan


### Maven Project Properties

- Check that (currently) latest stable version `2.23.1` of [Jersey](https://jersey.java.net/) is used and update if it's an older version.

{% highlight plain text %}
    <properties>
        <jersey.version>2.23.1</jersey.version>
    </properties>
{% endhighlight %}

- Commit this change to git.
- Set the [source and output encoding to UTF-8](http://verhagen.github.io/maven-project-properties/).
- Commit this change to git.


### Maven Plug-ins

- Update the version of the Maven compiler plug-in version to `3.5.1` (currently latest version).

{% highlight plain text %}
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>3.5.1</version>
                <inherited>true</inherited>
                <configuration>
                    <source>1.7</source>
                    <target>1.7</target>
                </configuration>
            </plugin>
{% endhighlight %}

- Commit this change to git.


### Change the Java version to 1.8

The Maven archetype ``, does still use Java version 1.7, make the following changes, to update it to 1.8.

- Update the `source` and `target` version configured in the `maven-compiler-plugin`

{% highlight plain text %}
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>3.5.1</version>
                <inherited>true</inherited>
                <configuration>
                    <source>1.8</source>
                    <target>1.8</target>
                </configuration>
            </plugin>
{% endhighlight %}

- Do __NOT__ commit this change, but also modify the [Travis configuration](http://dojo-java-programming.github.io/continuous-integration-with-travis-ci/) to Java 1.8. 

- Now commit this change to git - which a message like `Updates to Java version 1.8`
