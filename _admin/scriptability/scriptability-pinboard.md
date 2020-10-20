---
title: [Migrate or restore Pinboards]
last_updated: 10/16/2020
summary: "You can export an entire ThoughtSpot Pinboard in a flat-file format. After optional modification, you can migrate it to a different cluster, or restore it to the same cluster."
sidebar: mydoc_sidebar
permalink: /:collection/:path.html
---

In ThoughtSpot, you can download Pinboards to a flat file in `TSL`, [ThoughtSpot's Scripting Language]({{ site.baseurl }}/admin/scriptability/tsl-pinboard.html), modify the file, and subsequently upload this file either to the same cluster, or to a different cluster.

This mechanism supports several scenarios that you may encounter:

- <strong>Migrating from a development environment to a production environment</strong> by downloading the file from the development cluster and uploading the same file to the production cluster
- <strong>Implementing metadata changes outside ThoughtSpot UI</strong>, such as replacing the underlying data source for the entire Pinboard, or replacing a single column from one data source with a column in another data source
- **Reusing existing objects to build new objects**, such as building two very similar objects based on a similar, pre-existing object.

## How to use Scriptability
Depending on how you want to use Scriptability, there are several workflows you can follow:
1. **Edit and update an existing object in the same cluster**: You can either
- [export](#pinboard-export) the object(s), edit the object(s) by modifying its [ThoughtSpot Scripting Language]({{ site.baseurl }}/admin/scriptability/tsl-pinboard.html) (`TSL`) representation, and [import](#pinboard-update) the updated file(s) to modify the existing object *or*
- edit the object(s) using the [in-app `TSL` editor](#edit-tsl) and publish the updated file(s).
2. **Migrate an existing object from one cluster to a new cluster**: [export](#pinboard-export) the object(s) and [import](#pinboard-migrate) the updated file(s) to the new cluster.
3. **Edit and migrate an existing object from one cluster to a new cluster**: You can either
- [export](#pinboard-export) the object(s), edit the object(s) by modifying its [ThoughtSpot Scripting Language]({{ site.baseurl }}/admin/scriptability/tsl-pinboard.html) (`TSL`) representation, and [import](#pinboard-migrate) the updated file(s) to the new cluster *or*
- edit the object(s) using the [in-app `TSL` editor](#edit-tsl), publish the updated file(s), [export](#pinboard-export) the object(s), and [import](#pinboard-migrate) the updated file(s) to the new cluster. Note that this workflow changes the object(s) in both clusters.

## Prerequisites

**Import**

| Import and create a new object without importing its dependents | Import and create a new object and its dependents | Import and update an existing object without dependents | Import and update an existing object with dependents |
| ---------- | ---- | --- | --- |
| The dependents must already exist in the cluster. You must have **view** permissions for the first-level dependent. For example, if you import a Pinboard that is built on a Worksheet that is built on a table, you must have **view** permission for the Worksheet. | None | **Edit** permission on the existing object. The dependents must already exist in the cluster. You must have **view** permissions for the first-level dependent. | **Edit** permission on the existing object(s). |

**Export**

| Export with dependents | Export without dependents |
| ---- | ---- |
| **View** permission on the object and all dependents. | **View** permission on the object and its first-level dependents. |

{% include note.html content="If you have a permissions issue with a particular object when you export multiple objects, or an object and its dependents, the complete export does not fail. The individual object does not export, and you receive an error message about this failure in the <code>Manifest</code> file in the zip file." %}

{: id="pinboard-export"}
## Export Pinboard
You can export [one Pinboard at a time](#export-one), or export [more than one Pinboard as a zip file](#export-zip-file). The zip file contains a document called the `Manifest` file, which defines the objects you exported, and their underlying data sources.

{: id="export-one"}
### Export one Pinboard
To export one Pinboard:

1. Navigate to the Pinboard you want to export.

2. Click the three-dot icon, and select **Export as TSL**.

    ![Export a Pinboard]({{ site.baseurl }}/images/scriptability-cloud-pinboard-export.png "Export a Pinboard")

{: id="export-zip-file"}
### Export multiple Pinboards
To export multiple Pinboards at a time, follow these steps:

1. Navigate to the **Pinboards** page from the top navigation bar.

    ![The top navigation bar]({{ site.baseurl }}/images/scriptability-cloud-nav.png "The top navigation bar")

2. Hover over the Pinboards you want to export, and click the empty checkboxes that appear.

3. Select the **Export** button.

    ![Export multiple Pinboards]({{ site.baseurl }}/images/scriptability-pinboard-export.png "Export multiple Pinboards")

4. Choose whether to export only the Pinboards, or the Pinboards and their underlying data sources:

    ![Choose what to export]({{ site.baseurl }}/images/scriptability-cloud-click-export.png "Choose what to export")

5. Click **Export**.

4. Open the downloaded `.tsl` zip file. The SpotApp zip file contains a document called the `Manifest` file, which defines the objects you exported, their underlying data sources, and any export errors. If an individual export fails, you can find an error message in the `Manifest` file. The zip file still exports, even if an individual object's export fails.

{: id="edit-tsl"}
## Edit the Pinboard TSL file
You can edit the `TSL` file in one of two ways. You can [export](#pinboard-export) the Pinboard(s) and edit the file(s) in any text editor, before you import it. Or, you can use the [in-app `TSL` editor](#tsl-editor) to edit, validate, and publish the Pinboard(s). Refer to [Pinboard TSL specification]({{ site.baseurl }}/admin/scriptability/tsl-pinboard.html) for information on syntax in the TSL files.

{: id="tsl-editor"}
## Edit, validate, and publish Pinboards using the TSL editor
You can access the TSL editor from the Pinboard list page, or from the Pinboard itself. To edit and update multiple objects using the TSL editor, access it from the object list page.

To use the TSL editor, follow these steps:

1. Navigate to the **Pinboard** page from the top navigation bar.

2. Click the name of the Pinboard you want to edit, or select multiple Pinboards by clicking on the checkboxes that appear when you hover over a Pinboard name.

3. From the Pinboard list page, select the **Edit TSL** button that appears when you select an Pinboard or Pinboards. From the Pinboard itself, select the ellipsis ![more options menu]({{ site.baseurl }}/images/icon-ellipses.png){: .inline} (more options) menu in the upper-right side of the screen, and select **Edit TSL**.

4. The TSL editor opens. Edit the TSL file(s), using the syntax specified in [Pinboard TSL specification]({{ site.baseurl }}/admin/scriptability/tsl-pinboard.html).

    The TSL editor has the following functions under the top menu:
    - **File**: Validate, Publish, and Exit editor. You can also validate and publish using the **validate** and **publish** buttons at the top right of the editor. You can also exit the editor using the X button at the top right corner. The system warns you if you try to exit with unsaved changes.
    - **Edit**: Undo, Redo, Cut, Copy, Select all, Fold, Fold all, Unfold, Unfold all, and Go to line. The **Fold** option compresses the lines in the file so you only see the first line of a section. **Go to line** opens a dialog box, where you can type in the number of the line you would like to go to. This is useful for long TSL files.
    - **Find**: Find and Find and replace. This functionality allows you to easily find words or parameters in the TSL file. You can also click on a word or parameter in the TSL editor, and the editor highlights all instances of that word.
    - **View**: Show/Hide errors, Show line numbers, and Hide line numbers. **Show/Hide errors** toggles the **Errors** sidebar on and off. The **Errors** sidebar does not appear until after you Validate a file, if there are errors in it.
    - **Help**: Documentation. This links to the [Worksheet TSL Specification]({{ site.baseurl }}/admin/worksheets/yaml-worksheet.html) documentation. Navigate to the correct TSL specification article, based on the object(s) you are editing.

5. When you finish editing the TSL file(s), select **Validate** in the top right corner. You must validate each file individually. A blue dot appears next to any file that contains changes.

    ![Validate the file]({{ site.baseurl }}/images/scriptability-tsl-editor-validate.png "Validate the file")

6. If you constructed the file(s) correctly, a green check mark appears next to the name of the file. If you did not construct the file(s) correctly, a red bar appears near the top of the screen, telling you that ThoughtSpot found errors in one or more files. Click **Show errors** to see the errors listed in the **Errors** sidebar.

    ![Review errors]({{ site.baseurl }}/images/scriptability-tsl-editor-errors.png "Review errors")

7. After validating,  select **Publish** in the top right corner, next to **Validate**. You must publish each file individually.

8. The system displays a **Publish status** dialog box. You can select **Open [object]** to open the object you just published in a new tab, or click **Close** to return to the TSL editor.

    ![Open the Pinboard or return to the TSL editor]({{ site.baseurl }}/images/scriptability-tsl-editor-publish-status.png "Open the Pinboard or return to the TSL editor")


{: id="pinboard-update"}
## Update a Pinboard
You can overwrite an existing Pinboard by downloading the `TSL` file, making any necessary changes, and then re-uploading the `TSL` file.

You can also update an object using the [TSL editor](#tsl-editor).

To update an existing Pinboard by downloading the TSL file and modifying it, follow these steps. In this case, we are updating a single Pinboard. You can update multiple objects at once by uploading them in .zip file format.

1. [Export the Pinboard](#pinboard-export) you want to update, as in steps 1 to 5 of the **Export Pinboard** section above.

2. Edit the file in a text editor.

1. Navigate to the **Pinboards** page from the top navigation bar.

2. Click the name of the object you want to edit.

3. Click the ellipsis ![more options menu]({{ site.baseurl }}/images/icon-ellipses.png){: .inline} (more options) menu in the upper-right side of the screen.

4. Select **Update from TSL**.

5. In the **Import** interface, click **Select .tsl or .zip files to upload**.

   ![Find the Worksheet TSL file]({{ site.baseurl }}/images/scriptability-worksheet-update-browse.png "Find the Worksheet TSL file")

6. In your file system, find and select the `TSL` file you edited.

8. If you constructed the file correctly, the **Import** interface displays a *Validation successful* message. You can now import the file.

9. If you uploaded a `.zip` file with multiple Pinboards, you can unselect any files in the `.zip` file you do not want to upload.

10. Click **Import selected files**.

    ![Import selected file]({{ site.baseurl }}/images/scriptability-migrate-import-selected.png "Import selected files")

11. The **Import Status** screen displays the status of the objects you imported. You can open the object(s) that you imported, or click **Done** to return to the main object page.

    ![Go to object]({{ site.baseurl }}/images/scriptability-migrate-answers-created.png "Go to object")

{: id="pinboard-migrate"}
## Migrate a Pinboard
To migrate a Pinboard from one cluster to another, follow these steps.

1. [Export the Pinboard](#pinboard-export) you want to move, as in steps 1 to 5 of the **Export Pinboard** section above.

    The Pinboard remains on the original cluster as well, unless you delete it.

2. Navigate to the cluster you want to add the object to.

3. Click **Pinboards** on the top navigation bar.

4. Select **Import TSL** from the right-hand corner of the screen.

6. In the **Import** interface, click **Select .tsl or .zip files to upload**.

6. In your file system, find and select the `TSL` file. The file uploads automatically.

8. If you constructed the file correctly, the **Import** interface displays a *Validation successful* message. You can now import the file.

9. If you uploaded a `.zip` file with multiple objects, you can unselect any files in the `.zip` file you do not want to upload.

10. Click **Import selected files**.

11. The **Import Status** screen displays the status of the objects you imported. You can open the object(s) that you imported, or click **Done** to return to the main object page.

## Limitations of working with TSL files
There are certain limitations to the changes you can apply by editing a Worksheet, Answer, Table, View, or Pinboard through TSL.

* Formulas and columns can either have a new name, or a new expression. You cannot change both, unless migrating or updating the worksheet two times.

* It is not possible to reverse the join direction in the TSL script.

* You cannot create new tables using Scriptability. You can only update existing tables.

* You can only change logical tables using Scriptability. You cannot change the physical version of the table that exists in a database. When you change the `column_name`, for example, the name changes in the application, but not in the physical table in the database.

* You cannot import manually compressed .zip files. You can only import .zip files that you exported from ThoughtSpot: either an object and its associated data sources, or multiple objects of the same type that you exported from the object list page.

## Related Information
- [Pinboard TSL specification]({{ site.baseurl }}/admin/scriptability/tsl-pinboard.html)