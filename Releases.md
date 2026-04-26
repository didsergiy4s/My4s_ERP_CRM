Here you'll find brief release descriptions.

Future releases will contain only the changed files from this release! If you have not changed anything in previous releases,
then simply copy the My4S folder from the new version into the main My4S folder.
If you have already made changes, check that your changes are included in the files of the new release. Otherwise you will overwrite your work! You cannot skip releases.
Copy them one by one as they appear.

v1.0.1 Changes in the file …/My4s/cf/Short.htm. In the ID_DB table, a new constant type was added.
The constant must describe the value of the constant; it can be a number, a string, or a JSON string that may describe several parameters.
When using constants you must know the string type and use it accordingly!

v1.0.2 Changes in the file …/My4s/cf/METADATA.htm.
The ID_DB table now supports filtering by type.

v1.0.3 Changes in the file …/My4s/js/Blob.js.
Clients can now work with the database across different time zones. Clients can be located in different countries or in one country with multiple time zones.
How do we store dates on the server? We do this: the server, irrespective of the time zone, is always tied to London’s zero time zone (winter only!). 
And for each client we always compute the offset relative to London (timezoneOffset) and adjust the client date by this offset when recording dates on the server.
When generating date-based reports, again using the offset, we obtain the report for the client’s time zone! By default the program is configured to operate in a single time zone.
In the Blob.js module at the very beginning there is a variable: let timezoneOffset = 0; If you assign this variable the value 1, the program will work with multiple time zones! Attention!
This constant cannot be changed during operation. It must be configured at the very start of implementing My4S!
All releases from v1.0.1 through v1.0.3 are included in a single zip file My4S_v1.0.3.zip!

v1.0.5 Changes in the files: DOCS_jrn.htm, DOCS_db.htm, All_db.js, All_dbdoc.js, print.js, Blob.js All_cfcf.js, All_dball.js, MyBase.json, MyDB.js Several minor bugs fixed.
A new capability for preparing templates (layouts) using Excel.xlsx has appeared.
Of course, a layout can also be prepared using HTML (by default in My4S this is simply a report on tabular parts created almost automatically,
but this is not always sufficient). Complex report layouts are often required (for example, layouts like “Tax Invoice” and others).
However, the time required to prepare such a layout using HTML will be many times longer than preparing such a report in Excel.
Information on working with Excel can be found in Help.PDF in the New branch (Excel).

v1.0.6 Changes in the files: print.js, MyDB.js, MyMETADATA.js, MyComand.js, MySelect.js Several minor bugs fixed. PDF printing logic improved.
_______________________________________________________________________________________

Attention!! starting from version v1.0.7, new releases will be provided here - this will be a link to Google Drive.

v1.0.7 This version will include the complete My4S folder.
If someone is just starting to work with the program, they can simply take and replace the My4S folder from this release!
Others can replace only the Start4s.js file. Google Drive link: 
https://drive.google.com/file/d/1fNOAwCdPIUYRy0LNjfCsV4rSEcXA3yKv/view?usp=drive_link
