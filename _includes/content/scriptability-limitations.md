* Formulas and columns can either have a new name, or a new expression. You cannot change both, unless migrating or updating the worksheet two times.

* It is not possible to reverse the join direction in the TML script.

* You cannot create new tables using Scriptability. You can only update existing tables.

* You can only change logical tables using Scriptability. You cannot change the physical version of the table that exists in a database. When you change the `column_name`, for example, the name changes in the application, but not in the physical table in the database.

* You cannot create Scriptable representations of R- or Python-powered visualizations.

* You cannot import manually compressed .zip files. You can only import .zip files that you exported from ThoughtSpot: a custom SpotApp, an object and its associated data sources, or multiple objects of the same type that you exported from the object list page.

* Joins only appear in the table TML file of the source table in a join, or the table on the Many side of a Many to One join. You can only add and edit table joins from the TML file of the table on the Many side of the join. This is a Beta feature; to enable it, [contact ThoughtSpot Support]({{ site.baseurl }}/admin/misc/contact.html). You cannot view or modify table-level joins from the destination table's TML file.

* You cannot modify joins at the table level from the Worksheet, View, or Answer TML file. You can only override the joins for that specific Worksheet, View, or Answer. To modify table-level joins, you must edit the source table's TML file. This is a Beta feature; to enable it, [contact ThoughtSpot Support]({{ site.baseurl }}/admin/misc/contact.html).

* You cannot use TML to alter which columns and tables are in an Embrace connection.

* You cannot directly edit a relationship definition. To alter a relationship definition, you must rename the join or create a new join.

* You cannot delete joins from the TML file. You must delete them in the UI.