---
layout: post
title: Requirements Continued
---
Based on the initial vague {% post_url 2016-05-04-requirements %} you probably have some questions. 


## Questions

__How to identify different rooms?__

- Each room has a location code (identification).
- Some rooms have a name.

__How big is the meeting room?__ 

- For every room the number of persons that can use it together (for a meeting) is known.

__Is the number of rooms / facilities known?__

- During startup of the service(s), the configuration of rooms and facilities can be loaded. 


## Sample Data

Below are three samples given of concrete data, for rooms and their possible facility.


__Sample 01__

<table>
  <tr>
    <td>Name</td><td>Location</td><td>Capacity</td><td>Facilities</td>
  </tr>
{% for room in site.data.sample-rooms-01 %}
  <tr>
    <td>{{ room.name }}</td><td>{{ room.location }}</td><td>{{ room.capacity }}</td><td>{{ room.facilities }}</td>
  </tr>
{% endfor %}
</table>

__Sample 02__

<table>
  <tr>
    <td>Name</td><td>Location</td><td>Capacity</td><td>Facilities</td>
  </tr>
{% for room in site.data.sample-rooms-02 %}
  <tr>
    <td>{{ room.name }}</td><td>{{ room.location }}</td><td>{{ room.capacity }}</td><td>{{ room.facilities }}</td>
  </tr>
{% endfor %}
</table>

__Sample 03__

<table>
  <tr>
    <td>Name</td><td>Location</td><td>Capacity</td><td>Facilities</td>
  </tr>
{% for room in site.data.sample-rooms-03 %}
  <tr>
    <td>{{ room.name }}</td><td>{{ room.location }}</td><td>{{ room.capacity }}</td><td>{{ room.facilities }}</td>
  </tr>
{% endfor %}
</table>


## Create Cucumber Features

{% highlight plain %}
Feature: Refund item

Scenario: Jeff returns a faulty microwave
    Given Jeff has bought a microwave for $100
    And he has a receipt
    When he returns the microwave
    Then Jeff should be refunded $100
{% endhighlight %}


### Feature - Xxx 

__Scenario__ - 

__Given__
__When__
__Then__

