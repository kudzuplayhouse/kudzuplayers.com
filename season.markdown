---
title: Shows
date: 2016-11-03 19:38:00 Z
---

<div>
{% for show in site.shows %}

    <div class="full-width">
        <div class="col-2">
            <img src="{{ show['small image'] }}" />
        </div>
        <div class="col-2">
            <h4> {{ show.title }}</h4>
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
{% endfor %}
</div>
