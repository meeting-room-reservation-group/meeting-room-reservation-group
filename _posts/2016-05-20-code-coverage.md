---
layout: post
title: Checking the Code Coverage - Eclipse
---
The [Code Coverage](http://martinfowler.com/bliki/TestCoverage.html) says something about the lines of program code
that are covered by tests. Only a developer/tester can say something about how good these tests are. 

As writer of the _unit test_ and the _code_, it is imported to see how much of the code is hit by the unit tests. 


## Action Plan

### Install the Emma Code Coverage Feature for Eclipse

- Use the [Eclipse Marketplace](http://marketplace.eclipse.org/) to
  [install the Code Coverage feature](http://verhagen.github.io/eclipse-tip-marketplace-add-emma/). 

### Run Code Coverage Check

- In the view _Project Explorer_ or _Package Explorer_, go to the _unit test_ classes.
- Use the context menu (on the `RoomRepositoryTest`): _Coverage As > JUnit Test_  
  [![Eclipse Run Cucumber Examples with JUnit]({{ site.url }}/images/eclipse/eclipse-code-coverage-emma-00-tn.jpeg)]({{ site.url }}/images/eclipse/eclipse-code-coverage-emma-00.jpeg)  
  When the _Coverage Run_ is finished, the view _Coverage_ shows the percentages of code that are covered by a _unit test_.  
  [![Eclipse Run Cucumber Examples with JUnit]({{ site.url }}/images/eclipse/eclipse-code-coverage-emma-01-tn.jpeg)]({{ site.url }}/images/eclipse/eclipse-code-coverage-emma-01.jpeg)  
  The class `RoomRepository` has a coverage of 71%, inspecting the related code, shows that there is no _unit tests_ that covers the two exception cases, in the method `public void add(final Room room)`  
  __A good moment to add the missing unit tests__


## Adding missing Unit Test Cases


### Discovering a Hidden Mistake

{% highlight plain text %}
	@Test(expected = IllegalArgumentException.class)
	public void createBasicRoomNegativeCapacity() throws Exception {
		String location = null;
		int capacity = -2;
		new Room(location, capacity);
	}
{% endhighlight %}