The latest release of ThoughtSpot Cloud contains several new and enhanced features.

<h3>New Home page</h3>

The ThoughtSpot <a href="{{ site.baseurl }}/end-user/thoughtspot-one/thoughtspot-one-homepage.html">Home page</a> allows you to access all your essential actions as a business user. You can:

<ul>
<li>Search across existing Answers and Pinboards</li>
<li>Search your data to create new Answers and Pinboards</li>
<li>View objects you viewed recently</li>
<li>View trending Pinboards and Answers</li>
<li>Filter existing objects by favorite, author, tag, or type of object</li>
<li>Sort existing objects by author, views, or most recently viewed</li>
<li>Bulk mark objects as favorites</li>
</ul>

<h3>Search existing Answers</h3>
In addition to the existing Search over data, this release gives business users easy <a href="{{ site.baseurl }}/end-user/search/search-answers.html">Search over existing Answers and Pinboards</a>. This  meets the users' information needs by making Answers searchable, sortable, and applying filters on relevance, recency, number of views, authorship, metrics used, and so on.

<h3>Stats and Trends for Search on Answers Pinboard</h3>
Use this default <a href="{{ site.baseurl }}/admin/thoughtspot-one/query-intelligence-pinboard.html">Pinboard</a> to analyze how users are searching your existing Answers and Pinboards, so you can determine what objects are the most popular and what assets you may need to create.

<h3>Disable Answer Search for specific Worksheets</h3>
When users search for existing Answers and Pinboards, the default experience is to search across all Worksheets that they have access to. You may not want users to search for existing Answer and Pinboards built on certain Worksheets that are works in progress or deprecated. You can disable searching for Answers on specific Worksheets. Refer to <a href="{{ site.baseurl }}/admin/thoughtspot-one/disable-discover-for-worksheet.html">Disable Answer Search</a>.

<h3>Linked Pinboard filters</h3>
You can now create one filter that filters visualizations based on multiple Worksheets by linking the Worksheet columns, at the Pinboard level. This is useful when you have a Pinboard built on multiple Worksheets, and you would like to filter on columns that are functionally the same, but exist in multiple Worksheets.<br><br>

Refer to <a href="{{ site.baseurl }}/complex-search/linked-filters.html">Linked Pinboard filters</a>.<br>

<h3>Selective Pinboard filters</h3>
You can now configure Pinboard filters to apply to specific visualizations that you choose. This is useful when you would like to filter some, but not all, visualizations in a Pinboard.<br><br>

Refer to <a href="{{ site.baseurl }}/complex-search/selective-filters.html">Selective Pinboard filters</a>.

<!--<h3>Enhanced data modeling capabilities</h3>
This release enables new data modeling capabilities. You can now:
<ul>
<li>Join a View to a table</li>
<li>Build a Worksheet on top of a View</li>
</ul>-->

<h3>Geomaps</h3>
ThoughtSpot's Geomaps now have more detailed geographic and infrastructural boundaries by default. This includes road names, cities, and so on.<br>

ThoughtSpot supports maps of many countries. See the complete list in the <a href="{{ site.baseurl }}/reference/geomap-reference.html">Geo Map Reference</a>.

<h3>Answer V2</h3>

<p>Answer V2 is in Beta. It is off by default in ThoughtSpot Cloud clusters. The Answer V2 feature set contains these elements:</p>

  <dl>
  <dlentry>
    <dt>Improved Formula Editor</dt>
    <dd>The new <a href="{{ site.baseurl }}/complex-search/how-to-add-formula.html">Formula Editor</a> includes multi-line support, and a cleaner, bigger, and more intuitive interface.</dd></dlentry>
  <dlentry>
    <dt>Analyst-authored queries</dt>
    <dd><a href="{{ site.baseurl }}/admin/ts-cloud/analyst-authored-queries.html">Search Assist: Analyst-authored queries</a> enable Analysts, or anyone who has <strong>edit</strong> access to a Worksheet, to create <a href="{{ site.baseurl }}/admin/ts-cloud/search-assist.html">Search Assist</a> sample queries based on their company data. This gives all users the opportunity to experience onboarding and training on data that is relevant to their work, and specific to their line of business.</dd></dlentry>
  <dlentry>
    <dt>Table configuration enhancements</dt>
    <dd><a href="{{ site.baseurl }}/end-user/search/about-tables.html">Table configuration enhancements</a> in this release include conditional and number formatting for table summaries. Also, conditional formatting for attributes and measures in table cells is now more intuitive and robust.</dd></dlentry>
</dl>

The following features are not available in the Beta version of Answer V2. To use these features, <a href="{{ site.baseurl }}/admin/misc/contact.html">contact ThoughtSpot support</a> to turn Answer V2 off for your company. You can turn Answer V2 feature set on or off individually, from the <strong>Data</strong> panel on the <strong>Search</strong> page: select <strong>Switch to classic</strong> to turn it off, or select <strong>Try Beta experience</strong> to turn it on.

Answer V2 features and limitations currently only affect searches and Answers, on the <strong>Search</strong> page and on the <strong>Answers</strong> page. For example, if Answer V2 is on, the new Formula Editor interface appears when you add a formula to a search, but not when you add a formula to a Worksheet. Similarly, with Answer V2 on, you can see existing Pivot tables in your Pinboards, but you cannot create new Pivot table visualizations.

<ul>
<li><a href="{{ site.baseurl }}/end-user/search/ask-an-expert.html">Ask an Expert</a></li>
<li><a href="{{ site.baseurl }}/end-user/r-scripts/about-r-in-thoughtspot.html">R scripts</a></li>
<li><a href="{{ site.baseurl }}/end-user/search/about-attributes-and-measures.html#query-details">Query visualizer</a></li>
<li><a href="{{ site.baseurl }}/complex-search/about-pivoting-a-table.html">Pivot tables</a></li>
<li><a href="{{ site.baseurl }}/end-user/search/about-sankey-charts.html">Sankey charts</a></li>
</ul>

<h3>Customize ThoughtSpot Help</h3>
You can now tailor the ThoughtSpot Help menu to your organization by customizing it from the Admin Console. When you configure these Help settings, you set system-wide defaults for all your users.

Refer to <a href="{{ site.baseurl }}/admin/ts-cloud/customize-help.html">Customize ThoughtSpot Help</a>.

<h3>User Adoption Pinboard</h3>
The <a href="{{ site.baseurl }}/admin/ts-cloud/user-adoption.html">User Adoption Pinboard</a> is now accessible from the Admin Console.