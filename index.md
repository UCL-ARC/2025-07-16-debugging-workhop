---
layout: workshop  # DON'T CHANGE THIS.
# More detailed instructions (including how to fill these variables for an
# online workshop) are available at
# https://carpentries.github.io/workshop-template/customization/index.html
venue: "University College London (UCL)"  # brief name of the institution that hosts the workshop without address (e.g., "Euphoric State University")
address: "Function Space, 1st Floor, 90 High Holborn, London WC1V 6LJ"        # full street address of workshop (e.g., "Room A, 123 Forth Street, Blimingen, Euphoria"), videoconferencing URL, or 'online'
country: "gb"  # lowercase two-letter ISO country code such as "fr" (see https://en.wikipedia.org/wiki/ISO_3166-1#Current_codes) for the institution that hosts the workshop
language: "en"  # lowercase two-letter ISO language code such as "fr" (see https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes) for the workshop
latitude: "51.5181549"  # decimal latitude of workshop venue (use https://www.latlong.net/)
longitude: "-0.120675"  # decimal longitude of the workshop venue (use https://www.latlong.net)
humandate: "Jul 16, 2025"  # human-readable dates for the workshop (e.g., "Feb 17-18, 2020")
humantime: "9:45 am - 5:00 pm BST"      # human-readable times for the workshop e.g., "9:00 am - 4:30 pm CEST (7:00 am - 2:30 pm UTC)"
startdate: 2025-07-16  # machine-readable start date for the workshop in YYYY-MM-DD format like 2015-01-01
enddate: 2025-07-16  # machine-readable end date for the workshop in YYYY-MM-DD format like 2015-01-02
instructor: ["Dr Krishnakumar Gopalakrishnan (Krishna)", "Dr Tom Meltzer", "Dr Greg Law"]  # boxed, comma-separated list of instructors' names as strings, like ["Kay McNulty", "Betty Jennings", "Betty Snyder"]
helper: ["Dr Mosè Giordano"]  # boxed, comma-separated list of helpers' names, like ["Marlyn Wescoff", "Fran Bilas", "Ruth Lichterman"]
email: ["krishna.kumar@ucl.ac.uk"]  # boxed, comma-separated list of contact email addresses for the host, lead instructor, or whoever else is handling questions, like ["marlyn.wescoff@example.org", "fran.bilas@example.org", "ruth.lichterman@example.org"]
# collaborative_notes:  # optional: URL for the workshop collaborative notes, e.g. an Etherpad or Google Docs document (e.g., https://pad.carpentries.org/2015-01-01-euphoria)
# eventbrite:  # optional: alphanumeric key for Eventbrite registration, e.g., "1234567890AB" (if Eventbrite is being used)
# tickettailor:         # Optional: url bit that points to tickettailor event "1234567/abc/1100"
# pretix: "ARC/2025-07-26-debugging-2"              # Optional: url bit that points to pretix event "organisation/eventid"
# what3words:  "kick.sands.parent"         # optional: what3words (https://what3words.com) address of the workshop venue, without leading slashes e.g. "globe.lessening.computers"
---

{% comment %}
Various booking systems are available. They are shown in the config above, if they are empty none will show below.
{% endcomment %}
{% if page.eventbrite %}
{% include booking/eventbrite.html %}
{% elsif page.tickettailor %}
{% include booking/tickettailor.html %}
{% elsif page.pretix %}
{% include booking/pretix.html %}
{% endif %}


<h2 id="general">General Information</h2>

{% comment %}
INTRODUCTION

Edit the general explanatory paragraph below if you want to change
the pitch.
{% endcomment %}

<p>
  The <a href="{{site.arc_website}}">Centre for Advanced Research Computing (ARC)</a>
  is UCL's research, innovation and service centre for the tools, practices and systems
  that enable computational science and digital scholarship.
  
  We are an innovative centre with both professional services and academic missions:
  <ul>
    <li>We provide advanced, reliable and secure digital research infrastructure to
      research groups in UCL and beyond.</li>
    <li>We are a laboratory for research, teaching and innovation in compute, data
      and software intensive research methods.</li>
  </ul>

  You can read more about <a href="{{site.arc_education_website}}" target="_blank"> what our
    Education team offers</a>.
</p>

{% comment %}
AUDIENCE

<p id="who">
  <strong>Who:</strong>
  The course is aimed at anyone with an interest and experience in source-level debugging of compiled software code. It is particularly of interest to researchers and developers who are interested in High Performance Computing.
  <strong>
  You will need to be comfortable using the UNIX command line to interact with a machine, before you start this course. You will also need a good background in either C, C++ or Fortran programming languages.
  </strong>
  The <a href="https://swcarpentry.github.io/shell-novice/" target="_blank">Introduction to the UNIX shell</a> Carpentries lesson is a suitable pre-requisite, and ARC typically run an instance of this course every term.
</p>

{% assign begin_address = page.address | slice: 0, 4 | downcase  %}
{% if page.address == "online" %}
{% assign online = "true_private" %}
{% elsif begin_address contains "http" %}
{% assign online = "true_public" %}
{% else %}
{% assign online = "false" %}
{% endif %}
{% if page.latitude and page.longitude and online == "false" %}
<p id="where">
  <strong>Where:</strong>
  {{page.address}}.
  Get directions with
  <a href="//www.openstreetmap.org/?mlat={{page.latitude}}&mlon={{page.longitude}}&zoom=16">OpenStreetMap</a>
  or
  <a href="//maps.google.com/maps?q={{page.latitude}},{{page.longitude}}">Google Maps</a>.
  {% if page.what3words %}
    What3Words location:
    <a href="https://what3words.com/{{page.what3words}}">///{{page.what3words}}</a>.
  {%endif %}
</p>
{% elsif online == "true_public" %}
<p id="where">
  <strong>Where:</strong>
  online at <a href="{{page.address}}">{{page.address}}</a>.
  If you need a password or other information to access the training,
  the instructor will pass it on to you before the workshop.
</p>
{% elsif online == "true_private" %}
<p id="where">
  <strong>Where:</strong> This training will take place online.
  The instructors will provide you with the information you will need to connect to this meeting.
</p>
{% endif %}

{% comment %}
DATE

This block displays the date and links to Google Calendar.
{% endcomment %}
{% if page.humandate %}
<p id="when">
  <strong>When:</strong>
  {{page.humandate}}; {{page.humantime}}
  {% include workshop_calendar.html %}
</p>
{% endif %}

{% comment %}
SPECIAL REQUIREMENTS

Modify the block below if there are any special requirements.
{% endcomment %}
<p id="requirements">
  <strong>Requirements:</strong>
  {% if online == "false" %}
    Participants must bring a laptop with a
    Mac, Linux, or Windows operating system (not a tablet, Chromebook, etc.) that they have administrative privileges on.
  {% else %}
    Participants must have access to a computer with a
    Mac, Linux, or Windows operating system (not a tablet, Chromebook, etc.) that they have administrative privileges on.
  {% endif %}
  They should have a few specific software packages installed (listed <a href="#setup">below</a>).
</p>

{% comment %}
ACCESSIBILITY

Modify the block below if there are any barriers to accessibility or
special instructions.
{% endcomment %}
<p id="accessibility">
  <strong>Accessibility:</strong>
  We are committed to making this workshop
  accessible to everybody. 
{% if online == "false" %}
  The workshop organizers have checked that:
<p>
  <ul>
    <li>The room is wheelchair / scooter accessible.</li>
    <li>Accessible restrooms are available.</li>
  </ul>
{% endif %}
</p>
<p>We are dedicated to providing a positive and accessible learning environment for all. 
  We do not require participants to provide documentation of disabilities or disclose any unnecessary personal information. 
  However, we do want to help create an inclusive, accessible experience for all participants. 
  We encourage you to share any information that would be helpful to make your Carpentries experience accessible.
  To request an accommodation for this workshop, please fill out the 
  <a href="https://carpentries.typeform.com/to/B2OSYaD0">accommodation request form</a>.
  If you have questions or need assistance with the accommodation form please <a href="mailto:team@carpentries.org">email us</a>.
</p>
<p>
  <a href="https://glosario.carpentries.org/">Glosario</a> is a multilingual glossary 
  for computing and data science terms. The glossary helps 
  learners attend workshops and use our lessons to make sense of computational and programming jargon written in English by offering it 
  in their native language. Translating data science terms also provides a teaching tool for Carpentries Instructors to reduce barriers 
  for their learners.
</p>

{% comment %}
CONTACT EMAIL ADDRESS

Display the contact email address set in the configuration file.
{% endcomment %}
<p id="contact">
  <strong>Contact:</strong>
  Please email
  {% if page.email %}
  {% for email in page.email %}
  {% if forloop.last and page.email.size > 1 %}
  or
  {% else %}
  {% unless forloop.first %}
  ,
  {% endunless %}
  {% endif %}
  <a href='mailto:{{email}}'>{{email}}</a>
  {% endfor %}
  {% else %}
  to-be-announced
  {% endif %}
  for more information.
</p>


<p id="who-can-attend">
    <strong>Who can attend?:</strong>
    This workshop is open to the public.
</p>

<hr/>


{% comment %}
SCHEDULE

Show the workshop's schedule.

Small changes to the schedule can be made by modifying the
`schedule.html` found in the `_includes` folder for your
workshop type (`swc`, `lc`, or `dc`). Edit the items and
times in the table to match your plans. You may also want to
change 'Day 1' and 'Day 2' to be actual dates or days of the
week.

For larger changes, a blank template for a 4-day workshop
(useful for online teaching for instance) can be found in
`_includes/custom-schedule.html`. Add the times, and what
you will be teaching to this file. You may also want to add
rows to the table if you wish to break down the schedule
further. To use this custom schedule here, replace the block
of code below the Schedule `<h2>` header below with
`{% include custom-schedule.html %}`.
{% endcomment %}

<h2 id="schedule">Schedule</h2>

{% if site.carpentry == "swc" %}
{% include swc/schedule.html %}
{% elsif site.carpentry == "dc" %}
{% include dc/schedule.html %}
{% elsif site.carpentry == "lc" %}
{% include lc/schedule.html %}
{% elsif site.carpentry == "ucl-arc-debugging" %}
{% include ucl-arc-debugging/schedule.html %}
{% elsif site.carpentry == "incubator" %}
This workshop is teaching a lesson in 
<a href="https://carpentries-incubator.org/">The Carpentries Incubator</a>. Please check <a href="{{site.incubator_lesson_site}}">the lesson homepage</a> for a list of lesson sections and estimated timings.
{% endif %}

{% comment %}
Edit/replace the text above if you want to include a schedule table.
See the contents of the _includes/custom-schedule.html file for an example of
how one of these schedule tables is constructed.
{% endcomment %}

{% if site.pilot %}
The lesson taught in this workshop is being piloted and a precise schedule is yet to be established. The workshop will include regular breaks. Please <a href="mailto:{{page.email}}">contact the workshop organisers</a> if you would like more information about the planned schedule.
{% endif %}

<hr/>


{% comment %}
SETUP

Delete irrelevant sections from the setup instructions.  Each
section is inside a 'div' without any classes to make the beginning
and end easier to find.

This is the other place where people frequently make mistakes, so
please preview your site before committing, and make sure to run
'tools/check' as well.
{% endcomment %}

<h2 id="setup">Setup</h2>

<p>
  To participate in this
  {% if site.carpentry == "swc" %}
  Debugging
  {% elsif site.carpentry == "dc" %}
  Data Carpentry
  {% elsif site.carpentry == "lc" %}
  Library Carpentry
  {% endif %}
  workshop,
  you will need access to software as described below.
  In addition, you will need an up-to-date web browser.
</p>

{% if online != "false" %}
{% include install_instructions/videoconferencing.html %}
{% endif %}

{% comment %}
These are the installation instructions for the tools used
during the workshop.
{% endcomment %}

{% if site.carpentry == "swc" %}
{% include swc/setup.html %}
{% elsif site.carpentry == "dc" %}
{% include dc/setup.html %}
{% elsif site.carpentry == "lc" %}
{% include lc/setup.html %}
{% elsif site.carpentry == "ucl-arc-debugging" %}
{% include ucl-arc-debugging/setup.html %}
{% elsif site.carpentry == "incubator" %}
Please check the "Setup" page of
<a href="{{site.incubator_lesson_site}}">the lesson homepage</a> for instructions to follow
to obtain the software and data you will need to follow the lesson.
{% endif %}
