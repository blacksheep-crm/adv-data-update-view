# adv-data-update-view

# STRICTLY EDUCATIONAL! DO NOT USE IN MISSION-CRITICAL ENVIRONMENTS!

Provided "as-is" by Jason M. Published here with Thanks.

# Installation:

1. Import sif file content
2. Register ADV Data Update Admin View with appropriate Responsibility
3. Add LOV_TYPE: ADV_DATA_UPDATE_MODE
4. Add LOVs "Update by Row Id" and "Query for records to update"

# Use Case: Headless Change Records feature

Data updates and corrections are a frequent activity in Production environments. The IT team must either provide dozens of list applet-based views that business administrators can leverage using Change Records, or (what likely happens most often) the IT team runs SQL scripts to modify the table records directly.

This project leverages Siebel's business object layer while providing extreme flexibility in selecting the recordsets to update.  This "Data Update Admin" view accommodates two common scenarios: 1) The business user has a specific list of records with unique values for each record (such as a workbook containing Row IDs and corresponding field values); or, 2) the user needs to set common values on all records matching a certain Type, Created Date, or other "search by" criteria.

# Features of the Data Update Admin view:
- Selectable mode to perform an update with supplied rows ("Update by Row Id") or by querying for any matching records and appying the same value to their fields ("Query for records to update").
- Much faster update performance than using Change Records due to commits occurring only after all rows have been successfully updated.
- When updating by Row Id, users may drag and drop record values from Excel into the Data Inputs list applet.
- Constrained display of valid Business Components for a selected Business Object; constrained display of valid base column-based fields within the selected Business Component.
- The Query fields ("Search For…") can use operators such as <=, <, >=, and > as well as OR conditions such as "New OR Closed" or "> 03/31/2023".

# Other Notes and Limitations:

For either Update Mode, a maximum of 10,000 records can be updated.  (This is based on Siebel’s behavior to limit result sets to 10,000.)

In the “Query for Records to Update” mode, up to 4 Query criteria may be provided.

Up to 4 fields on the matching records may be updated at a time.

The commit occurs after all records have been processed.  An error on any record will roll back changes to all records. (Thanks to the EAI Transaction Service)

If a table or a column is not exposed as a Business Component, this feature will not be able to search or update against it.

Use "Thin" or "Lite" versions of BCs with generic classes to avoid BC-layer read-only rules. For example, trying to update a record using BC "Service Request" once the Status is Closed will almost always result in an error.


