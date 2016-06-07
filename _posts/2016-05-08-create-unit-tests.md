---
layout: post
title: Create Unit Tests
---
After gathering the [requirements]({% post_url 2016-05-07-requirements-continued %}) it time to think about the
Unit Test Cases. From these initial requirements there are a few nouns, that everyone should have found.


## Action Plan

- Todo


- Add first test class `FacilityTest`

{% highlight plain text %}
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
		
		assertEquals("Computer with large screen", facility.getName());
	}

}
{% endhighlight %}

- Implement the missing class `Facility`, make sure it end up in the right directory, inside the project `src/main/java` (or move it there, if it is created under `src/test/java`).

