
__How to identify different rooms?__

- Each room has a location code (identification).
- Some rooms have a name.


## Sample Data

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


## Cucumber Features

### Feature - Xxx 

__Scenario__ - 

__Given__
__When__
__Then__

