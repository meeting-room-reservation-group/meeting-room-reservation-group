
__How to identify different rooms?__

- Each room has a location code (identification).
- Some rooms have a name.


## Sample Data

sss

<ul>
{% for room in site.data.sample-rooms-00 %}
  <li>
      {{ room.name }} | {{ room.location }} | {{ room.capacity }} | {{ room.facilities }}
  </li>
{% endfor %}
</ul>



### Scenario - 



