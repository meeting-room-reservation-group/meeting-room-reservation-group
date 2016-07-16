---
layout: post
title: Checking the Code Coverage - Maven
---
During development you like to see the results [Checking the Code Coverage]({% post_url 2016-05-20-code-coverage %}) in the development environment. But also when adding the code to the source code repository, the Continuous Integration build, should check the _Code Coverage_. This is done through the [JaCoCo Maven Plug-in](http://www.eclemma.org/jacoco/trunk/doc/).


## Action Plan

- Add the `jacoco-maven-plugin` to the Maven project file `pom.xml`

{% highlight plain text %}
            <plugin>
                <groupId>org.jacoco</groupId>
                <artifactId>jacoco-maven-plugin</artifactId>
                <version>0.7.7.201606060606</version>
                <executions>
                    <execution>
                        <id>default-prepare-agent</id>
                        <goals>
                            <goal>prepare-agent</goal>
                        </goals>
                    </execution>
                    <execution>
                        <id>default-report</id>
                        <phase>prepare-package</phase>
                        <goals>
                            <goal>report</goal>
                        </goals>
                    </execution>
                    <execution>
                        <id>default-check</id>
                        <goals>
                            <goal>check</goal>
                        </goals>
                        <configuration>
                        <rules>
                            <rule>
                                <element>BUNDLE</element>
                                <limits>
                                    <limit>
                                        <counter>INSTRUCTION</counter>
                                        <value>COVEREDRATIO</value>
                                        <minimum>0.80</minimum>
                                    </limit>
                                    <limit>
                                        <counter>COMPLEXITY</counter>
                                        <value>COVEREDRATIO</value>
                                        <minimum>0.60</minimum>
                                    </limit>
                                    <limit>
                                        <counter>CLASS</counter>
                                        <value>MISSEDCOUNT</value>
                                        <maximum>0</maximum>
                                    </limit>
                                </limits>
                            </rule>
                        </rules>
                        </configuration>
                    </execution>
                </executions>
            </plugin>
{% endhighlight %}

- Run Maven verify  
  `mvn clean verify`  
  This should give a HTML report in `target/site/jacoco/index.html`, which shows the details of the code coverage.
  [![Eclipse Run Code Coverage]({{ site.url }}/images/maven/jacoco-maven-plugin-report-00-tn.jpeg)]({{ site.url }}/images/maven/jacoco-maven-plugin-report-00.jpeg)
  
