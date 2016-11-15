---
title: Field Trip Request
date: 2016-11-15 00:38:00 Z
is hide_nav: true
---

#### Field Trip Booking Request Form

Please fill out and submit the form below. You will receive a confirmation email with details concerning your group's reservation and when and how to submit payment.

<form class="interest_form">
    <fieldset>
        <label for="organization_name">Organization Name:</label>
        <input type="text" name="organization_name" id="organization_name">
    </fieldset>
    <fieldset>
        <legend>Group Leader's Name</legend>
        <div class="col-2">
            <input type="text" name="leader_first_name" id="leader_first_name">
            <label for="leader_first_name">First</label>
        </div>
        <div class="col-2">
            <input type="text" name="leader_last_name" id="leader_last_name">
            <label for="leader_last_name">Last</label>
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
        <label for="number_of_students">Number of Students: (15 minimum)</label>
        <input type="text" name="number_of_students" id="number_of_students">
    </fieldset>
    <fieldset>
        <label for="number_of_students">Number of Teachers:</label>
        <input type="text" name="number_of_teachers" id="number_of_students">
    </fieldset>
    <fieldset>
        <label for="number_of_teachers">Number of Teachers:</label>
        <input type="text" name="number_of_teachers" id="number_of_teachers">
    </fieldset>
    <fieldset>
        <label for="number_of_guests">Number of Additional Guests:</label>
        <input type="text" name="number_of_guests" id="number_of_guests">
    </fieldset>
    <fieldset>
       <b>Indicate which performance of ROMEO & JULIET you are interested in attending so we can check availability.</b>
       <ul>
          <li>
             <label>Tuesday, January 24 at 8:45 a.m.<input type="checkbox" name="jan_24_0845" /></label>
          </li>
          <li>
             <label>Tuesday, January 24 at 11:30 a.m.<input type="checkbox" name="jan_24_1130" /></label>
          </li>
          <li>
             <label>Thursday, January 26 at 8:45 a.m.<input type="checkbox" name="jan_26_0845" /></label>
          </li>
          <li>
             <label>Thursday, January 26 at 11:30 a.m.<input type="checkbox" name="jan_26_1130" /></label>
          </li>
       </ul>
    </fieldset>
    <input type="submit" value="Submit">
    <input type="hidden" name="form_name" value="matinee_field_trip_form">
</form>

<script type="text/javascript">
    $(document).ready(function() {

        $(".interest_form").submit(function(e) {
            e.preventDefault();
            var formData = $(e.target).serializeArray().reduce(function(a,x) {

                a.data[x.name] = x.value;
                return a;

            }, {data: {}});

            var submitBtn = $('.interest_form input[type="submit"]');
            submitBtn.attr('disabled', 'disabled');

            $.ajax({
               url: 'https://c4fkmchy15.execute-api.us-east-1.amazonaws.com/prod/emailer',
               dataType: 'json',
               contentType: 'application/json',
               data: JSON.stringify(formData),
               success: function(data) {
                  var form = $('.interest_form');
                  form.before('<h3>Thanks for contacting us!</h3>');
                  form.hide();
               },
               error: function() {
                   submitBtn.removeAttr('disabled');
                   $('.interest_form').after('<h3>There was a problem, please try again later.</h3>');
               },
               method: 'POST'
            });

        });

    });
</script>