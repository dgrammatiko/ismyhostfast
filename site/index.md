---
layout: base.njk
---

<script class="data-json" type="application/json">{{ metadata.inlineJSON | dump | safe }}</script>
<script type="module" src="/assets/js/main.js?{{metadata.version}}"></script>

<h2>Leaderboard: July 2021</h2>

<div class="app-container"></div>

<section>
  <p>
    Are you looking for the rate of improvment per host?
    Check the timeline <a href="/archive">here</a>.
  </p>
</section>

<section>
  <p>
    See a missing hosting provider?
    <a href="https://github.com/rviscomi/ismyhostfastyet/blob/master/README.md#contribute">
      Please help us identify how to surface them here.
    </a>
  </p>
</section>

<section>
  <h2>How do you measure real-world Time to First Byte?</h2>

  <p>
    This report is powered by <a href="http://bit.ly/chrome-ux-report">Chrome User Experience Report</a>,
    which provides user experience metrics for how real-world Chrome users experience popular
    destinations on the web. As a result, this report does not rely on synthentic tests of
    each hosting provider, but instead provides insight into how real-world users experience
    the speed of sites hosted by various providers.
  </p>

  <h2>What is Time to First Byte?</h2>

  <p>
    TTFB is measured as the time from the start of navigation request until the time that the
    client receives the first byte of the response from the server. It includes network setup time
    (SSL, DNS, TCP) as well as server-side processing.
  </p>

  <img src="/assets/ttfb.png" loading="lazy" height="248" width="800" alt="Diagram showing TTFB as the network events from the prompt for unload to the response start">

  <p>
    As you can see in the <a href="https://w3c.github.io/navigation-timing/">Navigation Timing Level 2 draft spec</a>
    screenshot above, the metric is equivalent to <code>performance.getEntriesByType('navigation')[0].responseStart</code>.
  </p>

  <h2>How do you determine: Fast, Average, Slow?</h2>

  <p>
    The thresholds for fast/average/slow TTFB are 500 ms as the upper limit for fast TTFB and 1500 ms as the lower limit for slow TTFB.
  </p>

  <ul>
    <li>
      ???fast??? TTFB &lt; 500 ms is based on the <a href="https://developers.google.com/speed/docs/insights/Server">server responsiveness</a>
            best practice.
    </li>
    <li>
      ???slow??? TTFB &gt;= 1500 ms is based on the requirement for the fast First Contentful Paint (FCP) threshold
      to be &lt; 1800 ms. A server response that exceeds 1500 ms will not, in most cases, meet the fast FCP goal.
    </li>
  </ul>

  <p>
    The 75th percentile (p75) TTFB is analyzed for each website, which is determined to be fast or slow by where it falls between those thresholds.
  </p>

  <p>
    The percentages for each host are calculated by taking the number of websites whose p75 TTFB is fast, average, and slow, and dividing each by the total number of websites. A previous version of this report averaged all websites' TTFB experiences together into a big, muddled distribution. This new approach is more accurate since it counts websites, not averaged experiences.
  </p>

  <h2>What about other metrics, why just TTFB?</h2>

  <p>
    Chrome UX Report provides other metrics like First Paint, First Contentful Paint, First Input Delay,
    and others. We plan to add more metrics to this report in the future. If you would like to help out,
    please <a href="https://github.com/rviscomi/ismyhostfastyet">let us know on GitHub</a>.
  </p>

  <h2>How frequently is this reported updated?</h2>

  <p>
    Chrome UX Report publishes monthly datasets and this report is updated once a month based on that data.
  </p>

  <h2>How are the hosting providers detected?</h2>

  <p>
    Chrome UX Report does not provide an explicit dimension for which hosting provider
    is associated with each origin. To perform the classification we rely on another
    dataset: <a href="https://httparchive.org">HTTP Archive</a> crawls all of the origins provided
    in CrUX and runs logic to identify providers based on header signatures, DNS records, and other signals.
  </p>

  <p>
    For example, a response header of <code>X-Powered-By: HubSpot</code> for a website's HTML page indicates that
    it is hosted by HubSpot.
  </p>

  <p>
    Would you like to see a hosting provider included in this report that???s currently
    not on the list? Please <a href="https://github.com/rviscomi/ismyhostfastyet/blob/master/README.md#methodology">read more about our methodology</a>
    and <a href="https://github.com/rviscomi/ismyhostfastyet/">join us on GitHub</a> ??? we???d appreciate your help to
    allow us to expand coverage of this report!
  </p>

  <h2>What about <q>X</q> ?</h2>

  <p>Good question! Please <a href="https://github.com/rviscomi/ismyhostfastyet/issues">start a discussion</a> on GitHub, so we can answer it.</p>
</section>
