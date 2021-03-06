---
layout: post
title: Create Unit Tests
---
After gathering the [requirements]({% post_url 2016-05-07-requirements-continued %}) it time to think about the
Unit Test Cases. From these initial requirements there are a few nouns, that everyone should have found.


## Action Plan

- Create the unit test cases source directory `src/test/java`.

- Create the package `com.github.<user-id>.mrrs.domain`, in the new unit test sources directory.  
  Replace `<user-id>` with your github user name.


- Add first test class `FacilityTest`
- Use the Java template `test` in Eclipse (from JUnit 4), to create a new test method.
- There are now a lot of errors, this is because the JUnit 4 library is not yet imported.
- Add the missing dependency to the `pom.xml`

{% highlight java %}
package com.github.verhagen.mrrs.domain;

import static org.junit.Assert.*;

import org.junit.Test;

public class FacilityTest {

    @Test
    public void createComputerWithLargeScreen() throws Exception {
        Facitlity facility = new Facility("Computer with large screen");
        
        assertEquals("Computer with large screen", facility.getName());
    }


    @Test
    public void createWhiteborad() throws Exception {
        Facitlity facility = new Facility("Whiteboard");
        
        assertEquals("Whiteboard", facility.getName());
    }

}
{% endhighlight %}

- Implement the missing class `Facility`, make sure it end up in the right directory, inside the project `src/main/java` (or move it there, if it is created under `src/test/java`).



- Add another test class `RoomTest` begin with a positive test

{% highlight java %}
    @Test
    public void createBasicRoom() throws Exception {
        String name = "Berlin";
        String location = "01.02";
        int capacity = 12;
        Room room = new Room(name, location, capacity);
        
        assertEquals(room.getName(), name);
        assertEquals(room.getLocation(), location);
        assertEquals(room.getCapacity(), capacity);
    }
{% endhighlight %}

- Implement the class `Room`

- Add some unit tests which check, that the required fields are given and / or are valid. The reuired field are: `location` and `capacity`.

{% highlight java %}
    @Test(expected = IllegalArgumentException.class)
    public void createBasicRoomNoLocation() throws Exception {
        String location = null;
        int capacity = 12;
        new Room(location, capacity);
    }

    @Test(expected = IllegalArgumentException.class)
    public void createBasicRoomNegativeCapacity() throws Exception {
        String location = null;
        int capacity = -2;
        new Room(location, capacity);
    }
{% endhighlight %}

- Improve the implementation of `Room`


{% highlight java %}
{% endhighlight %}


- Add an unit test, where the room has facilities.

{% highlight java %}
    @Test
    public void createRoomWithFacilities() throws Exception {
        String name = "Moscow";
        String location = "02.04";
        int capacity = 10;
        Set<Facility> facilities = new TreeSet<>();
        facilities.add(new Facility("whiteboard"));
        facilities.add(new Facility("beamer"));
        Room room = new Room(name, location, capacity, facilities);
        
        assertEquals(room.getName(), name);
        assertEquals(room.getLocation(), location);
        assertEquals(room.getCapacity(), capacity);
        assertEquals(room.getFacilities(), facilities);
    }
{% endhighlight %}

- This unit test does not run, as it fails already, before the assertEquals!!!
- An extra function `compareTo(Facility other)` is needed, so facilities can be compared to each other. Meaning to order them. Which is needed when adding them to a set.
- Create a unit test for the new functionality, of the class `Facility`

{% highlight java %}
    @Test
    public void compare() throws Exception {
        Facility whiteboard = new Facility("whiteboard");
        Facility beamer = new Facility("beamer");
        assertTrue(whiteboard.compareTo(beamer) > 0);
        assertTrue(beamer.compareTo(whiteboard) < 0);
    }
{% endhighlight %}

- Add the implementation for `Facility`
- Add the implementation for `Room`
