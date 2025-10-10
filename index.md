---

layout: col-sidebar
title: OWASP Tirana
tags: appsec-tag
region: Europe
country: Albania
meetup-group: owasp-tirane-chapter

---

## Welcome
Welcome to OWASP Tirana, the first chapter in Albania and Western Balkans.

We started this because we believe in Security, believe that well designed software has security as an intrisic part of it. The Chapter was founded by
  <a href="https://www.linkedin.com/in/kreshnikrexha" target="_blank" rel="noopener noreferrer">Kreshnik Rexha</a>
  &amp;
  <a href="https://www.linkedin.com/in/mariokazazi" target="_blank" rel="noopener noreferrer">Mario Kazazi</a>.

Chapter Supporters
----------------
The following are the list of OWASP Corporate Members who have generously aligned themselves with the London chapter, therefore contributing funds to our chapter:

<table cellpadding="15" cellspacing="0">
<tr>
<td>
    <a href="https://www.squarevertex.ai"><img src="assets/images/sqvertexai-high-resolution-logo-2.png" alt="squarevertex"/></a>
</td>
<td>
    <a href="https://startupalbania.org"><img src="assets/images/ThoughtWorks-logo.png" alt="StartUp Albania"/></a>
</td>
<td>
    <a href="https://www.kineton.al"><img src="assets/images/IEDigital-logo.png" alt="Kineton Albania"/></a>
</td>
</tr>

</table>


## Participation
The Open Worldwide Application Security Project (OWASP) is a nonprofit foundation that works to improve the security of software. All of our projects, tools, documents, forums, and chapters are free and open to anyone interested in improving application security. 

Chapters are led by local leaders in accordance with the [Chapters Policy](/www-policy/operational/chapters). Financial contributions should only be made online using the authorized online donation button. 

Everyone is welcome and encouraged to participate in our [Projects](/projects/), [Local Chapters](/chapters/), [Events](/events/), [Online Groups](https://groups.google.com/a/owasp.com/){:target='_blank'}, and [Community Slack Channel](https://owasp.slack.com/){:target='_blank'}. We especially encourage diversity in all our initiatives. OWASP is a fantastic place to learn about application security, to network, and even to build your reputation as an expert. We also encourage you to be [become a member](/membership/) or consider a [donation](/donate/) to support our ongoing work.

## Next Meeting/Event
---------------------

<div id="next-event">Loading next event...</div>

<script>
async function loadMeetupEvent() {
  const groupUrl = "owasp-tirane-chapter";
  const res = await fetch(`https://api.meetup.com/${groupUrl}/events?&sign=true&photo-host=public&page=1`);
  const events = await res.json();
  if (events && events.length > 0) {
    const e = events[0];
    const eventHTML = `
      <p><strong><a href="${e.link}" target="_blank">${e.name}</a></strong></p>
      <p>${new Date(e.local_date + "T" + e.local_time).toLocaleString()}</p>
    `;
    document.getElementById("next-event").innerHTML = eventHTML;
  } else {
    document.getElementById("next-event").innerHTML = "No upcoming events found.";
  }
}
loadMeetupEvent();
</script>

{% comment %}

[Join our next Meetup →](https://www.meetup.com/owasp-tirane-chapter/?eventOrigin=home_groups_you_organize)

{% endcomment %}

``

-->
