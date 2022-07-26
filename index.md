---
layout: workshop      
venue: "대전 한밭대(HanBat University) N13 509호"
address: "125 Dongseo-daero, Yuseong-gu, Daejeon, Republic of Korea"
country: "kr"
language: "kr"
latitude: "36.329155"
longitude: "127.315777"
humandate: "Aug 18-19 2020"
humantime: "9:00 am - 4:30 pm KST (UTC+9)"    
startdate: 2022-08-18
enddate: 2022-08-19  
instructor: ["Kwangchun Lee"] 
helper: ["Choonghyun Ryu", "Jonghwa Shin"]
email: ["victor@r2bit.com"]
collaborative_notes: https://pad.carpentries.org/2022-08-18-hanbat
eventbrite: 390464669337
---


{% comment %}
Check DC curriculum
{% endcomment %}

{% if site.carpentry == "dc" %}
{% unless site.curriculum == "dc-astronomy" or site.curriculum == "dc-ecology" or site.curriculum == "dc-genomics" or site.curriculum == "dc-socsci" or site.curriculum == "dc-geospatial" %}
<div class="alert alert-warning">
It looks like you are setting up a website for a Data Carpentry curriculum but you haven't specified the curriculum type in the <code>_config.yml</code> file (current value in <code>_config.yml</code>: "<strong>{{ site.curriculum }}</strong>", possible values: <code>dc-astronomy</code>, <code>dc-ecology</code>, <code>dc-genomics</code>, <code>dc-socsci</code>, or <code>dc-geospatial</code>). After editing this file, you need to run <code>make serve</code> again to see the changes reflected.
</div>
{% endunless %}
{% endif %}

{% if page.eventbrite %}
<strong>Some adblockers block the registration window. If you do not see the
  registration box below, please check your adblocker settings.</strong>
<iframe
  src="https://www.eventbrite.com/tickets-external?eid={{page.eventbrite}}&ref=etckt"
  frameborder="0"
  width="100%"
  height="280px"
  scrolling="auto">
</iframe>
{% endif %}


<h2 id="general">일반 정보</h2>

{% comment %}
INTRODUCTION

Edit the general explanatory paragraph below if you want to change
the pitch.
{% endcomment %}
{% if site.carpentry == "swc" %}
{% include swc/intro.html %}
{% elsif site.carpentry == "dc" %}
{% include dc/intro.html %}
{% elsif site.carpentry == "lc" %}
{% include lc/intro.html %}
{% endif %}

{% if site.pilot %}
This is a pilot workshop, testing out a lesson that is still under development. The lesson authors would appreciate any feedback you can give them about the lesson content and suggestions for how it could be further improved.
{% endif %}

{% comment %}
AUDIENCE

Explain who your audience is.  (In particular, tell readers if the
workshop is only open to people from a particular institution.
{% endcomment %}
{% if site.carpentry == "swc" %}
{% include swc/who.html %}
{% elsif site.carpentry == "dc" %}
{% include dc/who.html %}
{% elsif site.carpentry == "lc" %}
{% include lc/who.html %}
{% endif %}

{% comment %}
LOCATION

This block displays the address and links to maps showing directions
if the latitude and longitude of the workshop have been set.  You
can use https://www.latlong.net/ to find the lat/long of an
address.
{% endcomment %}
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
  <strong>장소:</strong>
  {{page.address}}.
  <a href="//www.openstreetmap.org/?mlat={{page.latitude}}&mlon={{page.longitude}}&zoom=16">OpenStreetMap</a>
  혹은
  <a href="//maps.google.com/maps?q={{page.latitude}},{{page.longitude}}">Google Maps</a> 참조.
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
  <strong>일시:</strong>
  {{page.humandate}}.
  {% include workshop_calendar.html %}
</p>
{% endif %}

{% comment %}
SPECIAL REQUIREMENTS

Modify the block below if there are any special requirements.
{% endcomment %}
<p id="requirements">
  <strong>요구사항:</strong>
  {% if online == "false" %}
  
    Participants must bring a laptop with a
    Mac, Linux, or Windows operating system (not a tablet, Chromebook, etc.) that they have administrative privileges on.
  {% else %}
  워크샵 참석자는 관리자 권한을 갖는 맥/리눅스/윈도 운영체제를 탑재한 노트북을 지참하여 참석하여야 하며 가능하면 뜻을 같이 하는 친구와 함께 적극적인 참여를 권장합니다. 태블릿, 크롬북 등은 불가합니다.
  {% endif %}
  노트북에는 <a href="#setup">아래</a> 기술된 특정 소프트웨어 패키지를 설치해와야 합니다.
</p>

{% comment %}
ACCESSIBILITY

Modify the block below if there are any barriers to accessibility or
special instructions.
{% endcomment %}
<p id="accessibility">
  <strong>Accessibility:</strong>
{% if online == "false" %}
  We are committed to making this workshop
  accessible to everybody.  For workshops at a physical location, the workshop organizers have checked that:
</p>
<ul>
  <li>The room is wheelchair / scooter accessible.</li>
  <li>Accessible restrooms are available.</li>
</ul>
<p>
  Materials will be provided in advance of the workshop and
  large-print handouts are available if needed by notifying the
  organizers in advance.  If we can help making learning easier for
  you (e.g. sign-language interpreters, lactation facilities) please
  get in touch (using contact details below) and we will
  attempt to provide them.
</p>
{% else %}
  We are dedicated to providing a positive and accessible learning environment for all. Please
  notify the instructors in advance of the workshop if you require any accommodations or if there is
  anything we can do to make this workshop more accessible to you.
</p>
{% endif %}

{% comment %}
CONTACT EMAIL ADDRESS

Display the contact email address set in the configuration file.
{% endcomment %}
<p id="contact">
  <strong>연락처:</strong>
  전자우편
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
  {% endif %} 주소로 연락주세요.
</p>

<p id="roles">
  <strong>Roles:</strong>
  To learn more about the roles at the workshop (who will be doing what),
  refer to <a href="https://carpentries.org/workshop_faq/#what-are-the-roles-of-everyone-participating-in-a-workshop">our Workshop FAQ</a>.
</p>

{% comment %}
WHO CAN ATTEND?

If you would like to specify who can attend the workshop,
you can use the section below.

Move the 'endcomment' tag above the beginning of the following
<p> tag to make this section visible.

Edit the text to match who can attend the workshop. For instance:
- This workshop is open to affiliates to ABC university.
- This workshop is open to the public.
- If you are interested in attending this workshop, contact me@example.com
  for more information

<p id="who-can-attend">
    <strong>Who can attend?:</strong>
    This workshop is open to ....
</p>
{% endcomment %}

<hr/>


<h2 id="code-of-conduct">행동강령(Code of Conduct)</h2>

<p>
Everyone who participates in Carpentries activities is required to conform to the <a href="https://docs.carpentries.org/topic_folders/policies/code-of-conduct.html">Code of Conduct</a>. This document also outlines how to report an incident if needed.
</p>

<p class="text-center">
  <a href="https://goo.gl/forms/KoUfO53Za3apOuOK2">
    <button type="button" class="btn btn-info">Report a Code of Conduct Incident</button>
  </a>
</p>
<hr/>


<h2 id="collaborative_notes">공동 메모장(Collaborative Notes)</h2>

<p>
노트필기, 채팅, URL과 코드를 공유하는데 <a href="{{ page.collaborative_notes }}">collaborative document</a> 을 사용합니다. 강사를 포함한 누구나 워크샵 관련 참여자 모두에게 도움이 될 수 있는 사항을 남길 수 있습니다.
</p>
<hr/>


<hr/>


<h2 id="schedule">일정</h2>

{% include custom-schedule.html %}

<hr/>


<h2 id="setup">환경설정</h2>

<p>
  {% if site.carpentry == "swc" %}
  Software Carpentry
  {% elsif site.carpentry == "dc" %}
  Data Carpentry
  {% elsif site.carpentry == "lc" %}
  Library Carpentry
  {% endif %}
  (데이터 카펜트리) 워크샵에 참여하기 위해서, 다음에 기술된 소프트웨어 툴체인을 구축하여 
사전에 동작하게 만들 필요가 있다. 워크샵 시작전에 필요한 모든 소프트웨어가 설치되었는지 확인한다.
(적어도 소프트웨어를 다운로드하거나 인스톨러를 준비)
</p>
<p>
  데이터 카펜트리에서 
  <a href = "{{site.swc_github}}/workshop-template/wiki/Configuration-Problems-and-Solutions">환경설치 문제점과 해결책에 대한 위키 페이지</a>를 운영하고 있으니
  설치시 참조한다..
</p>

<h2 id="sponsor">후원</h2>

이 프로그램은 과학기술진흥기금 및 복권기금의 재원으로 운영되고, 과학기술정보통신부와 한국과학창의재단의 지원을 받아 수행된 성과물로 우리나라의 과학기술 발전과 사회적 가치 증진에 기여하고 있습니다.

<div class="row-fluid">
  <table class="table">
    <tr> 
      <td> 
          <img src="./fig/01.png" width="200">
      </td>
      <td>
          <img src="./fig/02.png" width ="200">
      </td>
      <td>
          <img src="./fig/03.png" width ="200">
      </td>
      <td>
          <img src="./fig/04.png" width ="200">
      </td>
      <td>
          <img src="./fig/daejeon.gif" width ="200">
      </td>
      <td>
          대전과학문화거점센터
      </td>
    </tr>
  </table>
</div>

