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

- Add these test to the class `RoomRepositoryTest` and fill in the details.

{% highlight java %}
    @Test
    public void addNull() throws Exception {
        expExcep.expect(IllegalArgumentException.class);
        expExcep.expectMessage(new IsEqual<String>("Argument 'room' should not be null."));
        
        // TODO Fill in the test case details
    }

    @Test
    public void addWithSameLocation() throws Exception {
        expExcep.expect(IllegalArgumentException.class);
        expExcep.expectMessage(new IsEqual<String>("There is already a room registered with the location '01.12'."
                + " Registered room details 'Copenhagen, 01.12, 8, [ white board ]'"));

        // TODO Fill in the test case details
    }
{% endhighlight %}

- Probably the class `Room` is missing a nice output string and will show something like `There is already a room registered with the location '01.12'. Registered room details 'com.github.verhagen.mrrs.domain.Room@40993028'`.  

- Creating a nice output text for an Object  
  Override the method `public String toString()`
  
{% highlight java %}
	@Override
	public String toString() {
		// TODO Fill in the details
	}
{% endhighlight %}


## Discovering a Hidden Mistake

- After adding the missing test cases and writing a nice output for the class `Room`, let run again the _Code Coverage_, but now over all the classes.
- Select in the view _Package Explorer_ or _Project Explorer_ the project `meeting-room-reservation-services`.
- Use the context menu: _Coverage As > JUnit Test_
- Now the class `RoomRepository` should be 100% covered
- Not all `src/main/java` classes are 100% covered. Inspect the class `Room`.  
  !  
  In the constructor of `Room` there is a check `capacity <= 0`, that is never hit with a value smaller or equal to `0`. Therefor the background of the inner if statement is red. Looking opening the class `RoomTest` reveals that there is a test case for this situation.

{% highlight java %}
    @Test(expected = IllegalArgumentException.class)
    public void createBasicRoomNegativeCapacity() throws Exception {
        String location = null;
        int capacity = -2;
        new Room(location, capacity);
    }
{% endhighlight %}

- Why is this not working as intended?
- How to fix the issue?
- What improvement(s) do you see?

## Is the Code Coverage now Up To Date ?

- Run the Code Coverage again over the hole code base (of the project `meeting-room-reservation-services`).
- Can the Code Coverage still be improved? (skip the class `MyResource`)
