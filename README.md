# adv-data-update-view

# STRICTLY EDUCATIONAL! DO NOT USE IN MISSION-CRITICAL ENVIRONMENTS!

Provided "as-is" by Jason M. Published here with Thanks.

# Installation:

1. Import sif file content
2. Register ADV Data Update Admin View with appropriate Responsibility
3. Add LOV_TYPE: ADV_DATA_UPDATE_MODE
4. Add LOVs "Update by Row Id" and "Query for records to update"

# Use Case: Headless Change Records feature

The business user has a specific list of records (think Row IDs and a few columns from a workbook); other times, they just know they need to fix all records of a certain Type created since a certain Date, or some other "search by" criteria.

# Notes and Limitations:

For either Update Mode, a maximum of 10,000 records can be updated.  (This is based on Siebel’s behavior to limit result sets to 10,000.)

In the “Query for Records to Update” mode, up to 4 Query criteria may be provided.

The Query fields ("Search For…") can use operators such as <=, <, >=, and > as well as OR conditions such as "New OR Closed" or "> 03/31/2023".

Up to 4 fields on the matching records may be updated at a time.

The commit occurs after all records have been processed.  An error on any record will roll back changes to all records. (Thanks to the EAI Transaction Service)

If a table or a column is not exposed as a Business Component, this feature will not be able to search or update against it.

Use "Thin" or "Lite" versions of BCs with generic classes to avoid BC-layer read-only rules. For example, trying to update a record using BC "Service Request" once the Status is Closed will almost always result in an error.


