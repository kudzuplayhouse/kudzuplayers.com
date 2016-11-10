---
title: Volunteer
date: 2016-11-06 21:23:00 Z
---

### Participate in Kudzu Productions

Kudzu Playhouse relies heavily on volunteers to help with our productions. Please complete this quick form and click Submit at the bottom if you are interested in volunteering.  For safety and liability reasons, you must meet the minimum age requirement for each area. 

If you have formal training or work experience in any area, please email a resume to <a href="mailto:kudzuplayhousems@gmail.com">kudzuplayhousems@gmail.com</a>.

---

#### Volunteer Opportunities

<form class="interest_form">
    <fieldset>
    <b>Please check all areas in which you are interested in volunteering</b>
    <ul>
        <li>
            <label>Stage Manager (16 yrs.)<input type="checkbox" name="stage_manager"></label>
        </li>
        <li>
            <label>Props (18 yrs.)<input type="checkbox" name="stage_props"></label>
        </li>
        <li>
            <label>Set Constructions (16 yrs.)<input type="checkbox" name="set_construction"></label>
        </li>
        <li>
            <label>Set Decoration/Painting (13 yrs.)<input type="checkbox" name="set_decoration"></label>
        </li>
        <li>
            <label>Costumes (13 yrs.)<input type="checkbox" name="costumes"></label>
        </li>
        <li>
            <label>Lighting (16 yrs.)<input type="checkbox" name="lighting"></label>
        </li>
        <li>
            <label>Sound (16 yrs.)<input type="checkbox" name="sound"></label>
        </li>
        <li>
            <label>Choreography (16 yrs.)<input type="checkbox" name="choreography"></label>
        </li>
        <li>
            <label>Hair &amp; Makeup (16 yrs.)<input type="checkbox" name="hair_makeup"></label>
        </li>
        <li>
            <label>Music/Vocals (16 yrs.)<input type="checkbox" name="music_vocals"></label>
        </li>
        <li>
            <label>Orchestra Member (16 yrs.)<input type="checkbox" name="orchestra"></label>
        </li>
        <li>
            <label>House Manager (16 yrs.)<input type="checkbox" name="house_manager"></label>
        </li>
        <li>
            <label>Backstage Crew (13 yrs.)<input type="checkbox" name="backstage_crew"></label>
        </li>
        <li>
            <label>Lobby Decoration (13 yrs.)<input type="checkbox" name="lobby_decoration"></label>
        </li>
        <li>
            <label>Usher/Tickets (13 yrs.)<input type="checkbox" name="usher_tickets"></label>
        </li>
        <li>
            <label>Fundraising (18 yrs.)<input type="checkbox" name="fundraising"></label>
        </li>
    </ul>
    </fieldset>
    <fieldset>
        <label for="volunteer_other">If Other, please specify:</label>
        <input type="text" name="volunteer_other" id="volunteer_other">
    </fieldset>
    <fieldset>
        <legend>Name</legend>
        <div class="col-2">
            <input type="text" name="first_name" id="first_name">
            <label for="first_name">First</label>
        </div>
        <div class="col-2">
            <input type="text" name="last_name" id="last_name">
            <label for="last_name">Last</label>
        </div>
    </fieldset>
    <fieldset>
        <label for="email">Email</label>
        <input type="email" name="email" id="email">
    </fieldset>
    <fieldset>
        <label for="phone">Phone</label>
        <input type="tel" name="phone" id="phone">
    </fieldset>
    <fieldset>
        <label for="exp">Experience</label>
        <textarea name="exp" id="exp" cols="60" rows="6"></textarea>
    </fieldset>
    <input type="submit" value="Submit">
    <input type="hidden" name="form_name" value="volunteer_form">
</form>

<script type="text/javascript">
    $(document).ready(function() {

        $(".interest_form").submit(function(e) {
            e.preventDefault();
            var formData = $(e.target).serializeArray().reduce(function(a,x) {

                a.data[x.name] = x.value;
                return a;

            }, {data: {}});

            $.ajax({
               url: 'https://c4fkmchy15.execute-api.us-east-1.amazonaws.com/prod/emailer',
               dataType: 'json',
               contentType: 'application/json',
               data: JSON.stringify(formData),
               success: function(data) {
                  console.dir(data);
               },
               method: 'POST'
            });

        });

    });
</script>