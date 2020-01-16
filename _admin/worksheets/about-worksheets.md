---
title: [Create and use worksheets]

last_updated: tbd
summary: "Worksheets are flat tables created by joining columns from a set of one or more tables or imported datasets. "
sidebar: mydoc_sidebar
permalink: /:collection/:path.html
---

After modeling the data, create worksheets to make searching easier. For example, a sales executive might need to search for information about retail sales. The required data could be contained in several tables (sales, customers, products, stores, etc.), with foreign key relationships between them. An administrator who is familiar with the data model can create a retail sales worksheet, that combines all of the related fact and dimension tables into a single, easy-to-use view, and share it with the sales executive. This provides access to the data without requiring an understanding of how it is structured.

## Guidelines for worksheets

Users are often unfamiliar with tables and how they are related to one another. A worksheet groups multiple related tables together in a logical way.  You might use a worksheet for these reasons:

-   To pre-join multiple tables together.
-   To give a user or group access to only part of the underlying data.
-   To include a derived column using a formula.
-   To rename columns to make the data easier to search.
-   To build in a specific filter or aggregation.
-   To give users a filtered set of data to search.

Typically, you create one worksheet for each set of fact and dimension tables. For example, you may have a sales fact table and an inventory fact table. Each of these fact tables shares common dimensions like date, region, and store. In this scenario, you would create two worksheets: sales and inventory. The following diagram depicts the workflow for creating the sales worksheet.

![]({{ site.baseurl }}/images/workflow_create_worksheet.png)

The process for creating a worksheet is:

1.  Decide which tables to use for the worksheet.

2.  Create a new worksheet.

3.  Add sources (tables) to the worksheet.

4.  Choose the [worksheet join rule](progressive-joins.html#).

5.  Select the columns to include.

6.  Optionally [modify the join types](mod-ws-internal-joins.html#) within the worksheet.

7.  Optionally [create formulas](create-formula.html#).

8.  Optionally [create worksheet filters](create-ws-filter.html#).

9.  Save the worksheet.

10.  [Share the worksheet with groups or users]({{ site.baseurl }}/admin/data-security/share-worksheets.html#).

## Create a worksheet

Create a worksheet to make the data easy for users to search. This process includes adding a new worksheet, after which you will choose the data sources to include in it.

To create a new worksheet:

1. Click **Data**, on the top navigation bar.

2. Click the ellipses icon ![more options menu icon]({{ site.baseurl }}/images/icon-ellipses.png){: .inline}, and select **Create worksheet**.

    ![]({{ site.baseurl }}/images/worksheet_create_icon.png)


## Add sources and columns to a worksheet

After creating a worksheet, you need to add the sources that contain the data. Sources is another name for tables. The sources you choose are typically related to one another by foreign keys.

To add the sources to the worksheet:

1.  Click the **+** icon.

    ![]({{ site.baseurl }}/images/worksheet_add_sources_link.png)

2. Check the box next to each of the sources you want to include in the worksheet.

    Note that the list of sources only shows the data sources on which you have view or edit privileges.

    ![]({{ site.baseurl }}/images/worksheet_choose_sources_from_2.5.png)

3. If you want to see what the data inside the sources looks like, click **Explore all data**.

4. Choose the [worksheet join rule](progressive-joins.html#).

5. If you want to disable [Row Level Security]({{ site.baseurl }}/admin/data-security/row-level-security.html#), for this worksheet, check the checkbox to disable it.

6. Click **CLOSE** to save your changes.

7. Expand the table names under **Columns** and select the columns to add to the worksheet, by doing any of the following:

    1. To add all of the columns from a table, click the table name and click **+ Add Columns**.

    2. To add a single column, double-click its name.

    3. To add multiple columns, Ctl+click each column you want to add and click **+ Add Columns**.

    Note that after you add a column, non-related tables (those without a primary/foreign key relationship) become hidden. If you are working with two tables that should be related, but are not, you can [add a relationship between them]({{ site.baseurl }}/admin/data-modeling/about-relationships.html#).

8.  (Optional) [modify the join types](mod-ws-internal-joins.html#) within the worksheet.

9.  (Optional) [create formulas](create-formula.html#).

10.  (Optional) [create worksheet filters](create-ws-filter.html#).

11. Click the ellipses icon ![more options menu icon]({{ site.baseurl }}/images/icon-ellipses.png){: .inline}, and select **Save**.

12. In the Save Worksheet window, enter a name and description for your worksheet and click **SAVE**.

13. (Optional) Click each column name and enter a more user-friendly name for searching. You can tab through the list of columns to rename them quickly.

14.  (Optional) If you want to add a prefix to the name of several columns, select them, click the **Add prefix** button, and type in the prefix.

     ![]({{ site.baseurl }}/images/worksheet_add_col_prefix.png "Add a prefix to column names")

15. Click the the ellipses icon ![more options menu icon]({{ site.baseurl }}/images/icon-ellipses.png){: .inline}, and select **Save**.

    ![]({{ site.baseurl }}/images/action_save_worksheet.png "Save a worksheet")

16.  [Share your worksheet]({{ site.baseurl }}/admin/data-security/share-worksheets.html#), if you want other people to be able to use it.

## Where to go next

-   **[How the worksheet join rule works]({{ site.baseurl }}/admin/worksheets/progressive-joins.html)**  
Use the worksheet join rule to specify when to apply joins when a search is done on a worksheet. You can either apply joins progressively, as each search term is added (recommended), or apply all joins to every search.