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

{% include chapter_events.html group=page.meetup-group %}

<p>
  <a href="https://www.meetup.com/owasp-tirane-chapter/events/" target="_blank" rel="noopener">
    View all upcoming events on our Meetup page →
  </a>
</p>

</div>

<style>
.owasp-card {
  border: 1px solid #e6e8ee;
  border-radius: 12px;
  padding: 16px 18px;
  background: #fff;
  box-shadow: 0 2px 10px rgba(0,0,0,.04);
  max-width: 720px;
}
.owasp-card__header { margin-bottom: 8px; }
.owasp-card__eyebrow {
  display: inline-block;
  font-size: 12px;
  letter-spacing: .08em;
  text-transform: uppercase;
  color: #2563eb; /* OWASP-ish blue */
  margin-bottom: 6px;
}
.owasp-card__title {
  margin: 0;
  font-size: 20px;
  line-height: 1.35;
  color: #0f172a;
}
.owasp-card__meta { margin: 10px 0 12px; color: #334155; }
.owasp-card__row { margin: 4px 0; }
.owasp-card__cta a {
  display: inline-block;
  background: #2563eb;
  color: #fff !important;
  text-decoration: none;
  padding: 10px 14px;
  border-radius: 8px;
  font-weight: 600;
}
.owasp-card__cta a:hover { filter: brightness(1.05); }
</style>

<script>
(async () => {
  // 1) Fetch Meetup group RSS via a CORS-friendly JSON gateway
  const rssUrl = encodeURIComponent('https://www.meetup.com/owasp-tirane-chapter/events/rss/');
  const api = `https://api.rss2json.com/v1/api.json?rss_url=${rssUrl}`;

  const titleEl = document.querySelector('#next-event-card .owasp-card__title');
  const dateEl  = document.getElementById('next-event-date');
  const venueEl = document.getElementById('next-event-venue');
  const linkEl  = document.getElementById('next-event-link');

  function formatDate(isoString) {
    try {
      // Use UK-style formatting; adjust if you prefer a different locale
      return new Date(isoString).toLocaleString('en-GB', {
        weekday: 'short', year: 'numeric', month: 'long', day: 'numeric',
        hour: '2-digit', minute: '2-digit'
      });
    } catch { return ''; }
  }

  function extractVenueFromDescription(html) {
    // Meetup RSS description often contains lines like:
    // "Where: <br/>Pyramid of Tirana, Tirana, Albania"  OR similar blocks.
    // We’ll strip tags and look for a line starting with "Where"
    const tmp = document.createElement('div');
    tmp.innerHTML = html || '';
    const text = tmp.textContent.replace(/\r/g,'').replace(/\t/g,'').trim();

    // Try a few heuristics
    const whereLine = (text.split('\n').map(s => s.trim()).find(l => /^where[:\s]/i.test(l))) || '';
    if (whereLine) {
      return whereLine.replace(/^where[:\s]*/i,'').trim();
    }

    // Fallback: look for a plausible location after 'Location'
    const locMatch = text.match(/location[:\s]+(.+)/i);
    if (locMatch && locMatch[1]) return locMatch[1].trim();

    // Last resort: try to find a line with a city-like token (very loose)
    const lines = text.split('\n').map(s => s.trim()).filter(Boolean);
    const guess = lines.find(l => /Tirana|Albania|Pyramid/i.test(l));
    return guess || 'Tirana, Albania';
  }

  try {
    const res = await fetch(api);
    if (!res.ok) throw new Error('Failed to load events feed');
    const data = await res.json();

    const item = (data.items && data.items[0]) || null;
    if (!item) {
      titleEl.textContent = 'No upcoming events';
      dateEl.textContent = '—';
      venueEl.textContent = '—';
      linkEl.href = 'https://www.meetup.com/owasp-tirane-chapter/events/';
      return;
    }

    titleEl.textContent = item.title || 'Upcoming OWASP Tirana Meetup';
    dateEl.textContent  = item.pubDate ? formatDate(item.pubDate) : 'TBA';
    venueEl.textContent = extractVenueFromDescription(item.description || '') || 'TBA';
    linkEl.href = item.link || 'https://www.meetup.com/owasp-tirane-chapter/events/';
  } catch (err) {
    titleEl.textContent = 'Could not load event';
    dateEl.textContent = '—';
    venueEl.textContent = '—';
    linkEl.href = 'https://www.meetup.com/owasp-tirane-chapter/events/';
    console.error(err);
  }
})();
</script>

{% comment %}
{% endcomment %}

``

-->
