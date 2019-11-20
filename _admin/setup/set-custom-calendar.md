---
title: [Set up a custom calendar]


sidebar: mydoc_sidebar
permalink: /:collection/:path.html
---
By default, ThoughtSpot's fiscal calendar begins on January 1st. If your company's
calendar starts on a different date, you can use a custom calendar to ensure
date searches in ThoughtSpot reflect your fiscal calendar.

[Date formulas with the `fiscal` option specified]({{ site.baseurl }}/advanced-search/formulas/date-formulas.html#fiscal-and-gregorian-calendars)
also reflect the fiscal year you set here.

When you create a custom calendar, you designate the month, day and year on which your
company's fiscal year begins and ends. When using your custom calendar, searches like **this quarter** or **q3**, conform to the fiscal quarter defined by the calendar. Existing worksheets, tables, views and pinboards also reflect that calendar. When you add a custom calendar, be sure to alert your users of the change and how it affects both current and saved searches.

## Setting up a custom calendar

To set up a custom calendar for your cluster, you must do the following:
1. Enable the custom calendar feature.
2. Generate a calendar template.
3. Edit the calendar template.
4. Add the custom calendar to your cluster.

### Enable the custom calendar feature

To enable the custom calendar feature for your cluster, contact [ThoughtSpot Support]({{ site.baseurl }}/admin/misc/contact.html#).

### Generate a calendar template

Using a calendar template as your starting point ensures that you use a format that is compatible with ThoughtSpot.

To generate a calendar template, do the following:

1. SSH as admin into your ThoughtSpot cluster: `ssh admin@<cluster-ip-address or hostname>`.

2. Run the `tscli calendar generate` command using the following syntax:

      `tscli calendar generate --name <calendar_name> --start_date <MM/DD/YYYY> --end_date <MM/DD/YYYY> --username tsadmin`

      Example:
      `tscli calendar generate --name my_calendar --start_date 07/01/2019 --end_date 06/30/2020 --username tsadmin`

      This generates a calendar template file in .csv format. In the previous example: **my_calendar.csv**.

3. Exit your SSH session.

### Edit the calendar template

To use the template you generated as your custom calendar, some editing is required.

1. Download the .csv file to your computer using following syntax:

      `scp admin@<cluster-ip-address>:/home/admin/<calendar_name>.csv /<Local directory on your computer>/.`

      Example (on Mac OS):
      `scp admin@172.18.144.217:/home/admin/my_calendar.csv /Users/john.smith/Desktop/.`

2. Open the .csv file in a text editor or spreadsheet program and edit the file to ensure the date and quarter columns are formatted correctly:
  - The Date column must use the format: **MM/DD/YYYY**. No other formats are supported.
  - The Quarter column must display the correct quarter number for each day of the year.

        {% include note.html content="By default, a generated calendar displays quarter numbers based on the Gregorian calendar (which starts on January 1st). If your custom calendar begins any other date, you must adjust the quarter numbers to align with your calendar. For example: If your custom calendar begins on April 1st, the calendar would incorrectly show April, May and June as quarter 2. You would need to correct this to indicate those months are quarter 1 and correct the subsequent months to have the correct quarter." %}
      - (Optional) To enhance searchability, ThoughtSpot recommends adding a “Q” before each quarter number. Example: **Q1**. If adapting the calendar to different language, use the appropriate letter in place of "Q".
      - Make any other changes needed to the calendar (like translating months or days into a different language.)

    Example calendar with the fiscal year beginning on April 1:
    ![]({{ site.baseurl }}/images/custom_cal.png)

3. Save your calendar template as a UTF-encoded .csv file with UNIX line breaks.

      {% include note.html content="Saving the file with UNIX line breaks, ensures there are no carriage returns (^M characters) in the file which prevent you from using your calendar in ThoughtSpot. Microsoft Excel, for example, adds carriage returns. The easiest way to remove carriage returns is to open your .csv file in a text editor, and save it as a .csv with UNIX line breaks." %}

### Add the custom calendar to your cluster

To use your edited calendar template as a custom calendar, you must upload it to your cluster and use it to create a calendar in ThoughtSpot.

1. Upload the .csv file to your ThoughtSpot cluster using the following syntax:

      `scp /<Local directory on your computer>/<calendar_template_name>.csv admin@<cluster-ip-address>:/home/admin/`

      Example (on Mac OS):
      `scp /Users/john.smith/Desktop/my_calendar.csv admin@172.18.144.217:/home/admin`

2. SSH as admin into your ThoughtSpot cluster: `ssh admin@<cluster-ip-address or hostname>`.

3. Run the `tscli calendar create` command using the following syntax:
   `tscli calendar create --file_path /home/admin/<calendar_template_name>.csv --name <calendar name> --username tsadmin`

   Example:
   `tscli calendar create --file_path /home/admin/my_calendar.csv --name my_calendar --username tsadmin`

### (Optional) Set a custom calendar as the default calendar for your cluster

To set your custom calendar as the default calendar for your cluster, contact [ThoughtSpot Support]({{ site.baseurl }}/admin/misc/contact.html#).

## Setting a worksheet, table or view to use your custom calendar

If you don't set your custom calendar as the default for your cluster, you must do the following to use your calendar:

1. Sign in to your ThoughtSpot cluster and click **DATA**.

2. On the DATA page, click the name of a worksheet, table or view in which you want to use your custom calendar.

3. Under COLUMN NAME, find a column that uses the DATE or DATE_TIME data type where you want to use your custom calendar and scroll right until you see the CALENDAR TYPE column.

    {% include note.html content="The column must use the DATE or DATE_TIME data type." %}

4. In the CALENDAR TYPE column for the column(s) you chose, double-click the existing calendar name, and then select your custom calendar.

5. Click **Save Changes**.

  Now, date-related searches in the selected worksheet, table or view use your custom calendar.