---
layout: workshop  # DON'T CHANGE THIS.
# More detailed instructions (including how to fill these variables for an
# online workshop) are available at
# https://carpentries.github.io/workshop-template/customization/index.html
venue: "Debugging Workshop at UCL"  # brief name of the institution that hosts the workshop without address (e.g., "Euphoric State University")
address: "Function Space, 1st Floor, 90 High Holborn, London WC1V 6LJ"        # full street address of workshop (e.g., "Room A, 123 Forth Street, Blimingen, Euphoria"), videoconferencing URL, or 'online'
country: "gb"  # lowercase two-letter ISO country code such as "fr" (see https://en.wikipedia.org/wiki/ISO_3166-1#Current_codes) for the institution that hosts the workshop
language: "en"  # lowercase two-letter ISO language code such as "fr" (see https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes) for the workshop
latitude: "51.518010"  # decimal latitude of workshop venue (use https://www.latlong.net/)
longitude: "-0.117956"  # decimal longitude of the workshop venue (use https://www.latlong.net)
humandate: "Jul 16, 2025"  # human-readable dates for the workshop (e.g., "Feb 17-18, 2020")
humantime: "9:45 am - 5:00 pm BST"      # human-readable times for the workshop e.g., "9:00 am - 4:30 pm CEST (7:00 am - 2:30 pm UTC)"
startdate: 2025-07-16  # machine-readable start date for the workshop in YYYY-MM-DD format like 2015-01-01
enddate: 2025-07-16  # machine-readable end date for the workshop in YYYY-MM-DD format like 2015-01-02
instructor: ["Dr Krishnakumar Gopalakrishnan (Krishna)", "Dr Tom Meltzer", "Dr Greg Law", "Dean Stewart", "Will De Figueira"]  # boxed, comma-separated list of instructors' names as strings, like ["Kay McNulty", "Betty Jennings", "Betty Snyder"]
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
  We encourage you to share any information that would be helpful to make your experience accessible.
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


<h2 id="schedule">Schedule</h2>

<div class="row">       
  <div class="col-12">
  <div style="overflow-x: auto;">  <!-- added this wrapper for horizontal scrolling -->
  <table class="table table-striped" style="min-width: 600px; width: 100%; table-layout: fixed;"> <!-- added inline style -->
  <thead>
  <tr>
  <th style="width: 15%;">Time</th>
  <th style="width: 10%;">Duration</th>
  <th style="width: 75%;">Lesson / Activity</th>
  </tr>
  </thead>
  <tbody>
  <tr>
  <td>09:45 – 10:15</td>
  <td>30 min</td>
  <td>Welcome, coffee/tea/pastries, intro to the workshop, logistics, schedule, software and environment setup help on user laptops</td>
  </tr>
  <tr>
  <td>10:15 – 11:20</td>
  <td>1 hr 5 min</td>
  <td>Exercises on command-line debugging of serial programs (Instructor: Krishna)</td>
  </tr>
  <tr>
  <td>11:20 – 11:30</td>
  <td>10 min</td>
  <td>Break</td>
  </tr>
  <tr>
  <td>11:30 – 12:00</td>
  <td>30 min</td>
  <td>Demonstration of reverse debugging capabilities of open source debuggers (Instructor: Krishna)</td>
  </tr>
  <tr>
  <td>12:00 – 12:25</td>
  <td>25 min</td>
  <td>Introduction to parallel (multi-core, multi-node) debugging principles and introduction to the <code>mdb</code> debugger (Instructor: Tom Meltzer)</td>
  </tr>
  <tr>
  <td>12:25 – 12:55</td>
  <td>30 min</td>
  <td>Exercise on multi-core debugging on laptops (Instructor: Tom Meltzer)</td>
  </tr>
  <tr>
  <td>12:55 – 13:00</td>
  <td>5 min</td>
  <td>Fold away the tables and vacate the room (another event is scheduled in the room)</td>
  </tr>
  <tr>
  <td>14:00 – 14:05</td>
  <td>5 min</td>
  <td>Return to room and setup the tables to continue the debugging workshop</td>
  </tr>
  <tr>
  <td>14:05 – 14:15</td>
  <td>10 min</td>
  <td>Sort out HPC access and pair up participants without HPC access</td>
  </tr>
  <tr>
  <td>14:15 – 15:15</td>
  <td>1 hr</td>
  <td>Intermediate <code>mdb</code> exercises: multi-node, GPU, BYOC (bring your own codes) debugging (Instructor: Tom Meltzer)</td>
  </tr>
  <tr>
  <td>15:15 – 15:25</td>
  <td>10 min</td>
  <td>Coffee break</td>
  </tr>
  <tr>
  <td>15:25 – 15:50</td>
  <td>25 min</td>
  <td>Principles of time-travel (reverse) debugging (Instructor: Greg Law, undo.io)</td>
  </tr>
  <tr>
  <td>15:50 – 16:00</td>
  <td>10 min</td>
  <td>Setup Perforce TotalView demo license on users’ machines and help with installs</td>
  </tr>
  <tr>
  <td>16:00 – 16:55</td>
  <td>55 min</td>
  <td>Reverse debugging exercises with the TotalView Debugger (Instructors: Dean Stewart and Will De Figueira, Perforce)</td>
  </tr>
  <tr>
  <td>16:55 – 17:00</td>
  <td>5 min</td>
  <td>Concluding remarks, advanced exercises, further learning resources, next steps</td>
  </tr>
  </tbody>
  </table>
  </div>
  </div>
</div>

The room has been reserved until 6 PM for those interested to stay back, ask questions, interact with speakers or other participants or continue to do exercises.

<h2 id="setup">Setup</h2>

<h3 id="winsetup">Microsoft Windows</h3>
Windows users should install [WSL2 and any Linux distro](https://learn.microsoft.com/en-us/windows/wsl/install) and follow the *nix instructions <a href="#nixdarwinsetup">below</a> after launching a bash shell session within WSL2.

<h3 id="nixdarwinsetup">Linux and macOS Users</h3>
<p>Follow these steps to install all required tools for the workshop using <strong>Pixi</strong> on Linux and macOS (Apple Silicon &amp; Intel):</p>
<ol>
  <li><strong>Install Pixi</strong> by running this command in your terminal:<br>
    <pre><code class="language-bash">curl -fsSL https://pixi.sh/install.sh | sh</code></pre>
  </li>
  <li><strong>Restart your terminal or shell</strong> to apply the changes.</li>
  <li><strong>Get the workshop files</strong> by cloning or downloading the exercise repository:<br>
    <pre><code class="language-bash">git clone https://github.com/Cambridge-ICCS/summer-school-debugging.git
cd summer-school-debugging</code></pre>
  </li>
  <li><strong>Download the <a href="./pyproject.toml" download><code>pyproject.toml</code></strong> file into your working directory (where you run Pixi):<br>
    You can download it from the repository or place it manually in the folder.
  </li>
  <li><strong>Launch the Pixi shell</strong> to enter an environment with all tools installed:<br>
    <pre><code class="language-bash">pixi shell</code></pre>
  </li>
</ol>
<p>All the necessary tools and packages will now be available inside this shell session.</p>

