---
title: Shows
date: 2016-11-03 19:38:00 Z
---

<div class="shows">
{% for show in site.shows %}
    {% if show.season == "2016" %}
    <div class="full-width">
        <div class="col-2">
            <a href="{{ show.url }}">
            <img src="{{ show['small image'] }}" />
            </a>
        </div>
        <div class="col-2">
            <a href="{{ show.url }}"><h4> {{ show.title }}</h4></a>
            <p>
            Directed by {{ show.director }}
            </p>
            <p>
            {{ show.show_dates }}
            </p>
            {{ show.venue }}
            <p>
            {% if show['is kidzu'] == true %}
            (Kidzu Playhouse Production, Rated {{ show.rating }})
            {% else %}
            (Kudzu Playhouse Production, Rated {{ show.rating }})
            {% endif %}
            </p>
            <p>
            {{ show.hashtag }}
            </p>
            <p>
            <em>{{ show.special_arrangments }}</em>
            </p>
        </div>
    </div>
    <hr>
  {% endif %}
{% endfor %}
</div>
