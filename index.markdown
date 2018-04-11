---
layout: default
title: Welcome
---

# {{ page.title }}

to the _IBM Cloud_ Meetup at the University of Stuttgart.

## Labs

{% for lab in site.labs %}
  1. [{{ lab.title }}]({{ site.baseurl }}{{ lab.url }})
{% endfor %}


<br><br>
## This site can be found here: <span style="color:orange">http://bit.ly/MeetupStuttgart</span>
