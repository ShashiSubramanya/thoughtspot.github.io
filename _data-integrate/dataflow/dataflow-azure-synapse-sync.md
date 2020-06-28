---
title: [Sync data through Azure Synapse connection]
last_updated: 6/17/2020
toc: true
sidebar: mydoc_sidebar
permalink: /:collection/:path.html
---
After using ThoughtSpot DataFlow to establish a connection to an Azure Synapse database, you can create automatic data updates, to seamlessly refresh your data.

To sync your data, follow these steps:

{% include content/dataflow/sync-database.md %}

4. Specify the sync properties:

   <!--![Enter connection details]({{ site.baseurl }}/images/dataflow-azure-synapse-create.png "Enter connection details")-->

   * [Data extraction mode]({{ site.baseurl }}/data-integrate/dataflow/dataflow-azure-synapse-reference.html#dataflow-azure-synapse-sync-data-extraction-mode)<br/>Specify the extraction type.<br/>Mandatory field.
   * [Column delimiter]({{ site.baseurl }}/data-integrate/dataflow/dataflow-azure-synapse-reference.html#dataflow-azure-synapse-sync-column-delimiter)<br/>Specify the column delimiter character.<br/>Mandatory field.
   * [Null value]({{ site.baseurl }}/data-integrate/dataflow/dataflow-azure-synapse-reference.html#dataflow-azure-synapse-sync-null-value)<br/>Specify the string literal that represents NULL on the source. When loading data, the system replaces this with NULL.<br/>Optional field.
   * [Text qualifier]({{ site.baseurl }}/data-integrate/dataflow/dataflow-azure-synapse-reference.html#dataflow-azure-synapse-sync-text-qualifier)<br/>Specify if text columns in the source data are enclosed in quotes; if yes, single quotes or double quoates.<br/>Optional field.
   * [Escape character]({{ site.baseurl }}/data-integrate/dataflow/dataflow-azure-synapse-reference.html#dataflow-azure-synapse-sync-escape-character)<br/>Specify this character to escpate text qualifiers in source data.<br/>Optional field.
   * [Fetch size]({{ site.baseurl }}/data-integrate/dataflow/dataflow-azure-synapse-reference.html#dataflow-azure-synapse-sync-fetch-size)<br/>Specify the number of rows fetched into memory at the same time. If the value is 0, system fetches all rows at the same time.<br/>Mandatory field.
   * [TS load options]({{ site.baseurl }}/data-integrate/dataflow/dataflow-azure-synapse-reference.html#dataflow-azure-synapse-sync-ts-load-options)<br/>Specify additional parameters passed with the <code>tsload</code> command. The format for these parameters is:<br/><code>--&lt;param_1_name&gt; &lt;optional_param_1_value&gt;</code><br/>Optional field.

   See [Sync properties]({{ site.baseurl }}/data-integrate/dataflow/dataflow-azure-synapse-reference.html#sync-properties).