Brief release descriptions will appear here.

Future releases will only contain the changed files from this release! If you haven't changed anything in previous releases,
then simply copy the My4S folder from the new release to the main My4S folder. If you've already changed something, then check whether your changes are included in the new release's files.
Otherwise, you'll overwrite your work!
You can't skip releases. Copy them one by one, as they appear.

v1.0.1 Changes in file .../My4s/cf/Short.htm. A new const type has been added to the ID_DB table.
A const must describe the value of the constant; it can be a number, a string, or a JSON string that can describe multiple parameters.
When using constants, you must know the string type and use it accordingly!

v1.0.2 Changes in file .../My4s/cf/METADATA.htm. The ID_DB table now supports filtering by type.

v1.0.3 Changes in file .../My4s/js/Blob.js. Clients can now work with the database across time zones.
Clients can be located in different countries or in a single country with multiple time zones. How do we store dates on the server?
We do this: the server, regardless of the time zone, is always linked to London's zero time zone (winter only!).
And for each client, we always calculate the offset relative to London (timezoneOffset) and adjust the client's date by this offset when writing dates to the server.
When receiving date reports, again using the offset, we get a report for the client's time zone!
By default, the program is configured to work in a single time zone. In the Blob.js module, at the very beginning, there is a variable: let timezoneOffset = 0;
If you assign this variable a value of 1, then the program will work with multiple time zones!
Attention! This constant cannot be changed during operation. It must be configured at the very beginning of the My4S implementation!
All releases from v1.0.1 to v1.0.3 are included in a single zip file, My4S_v1.0.3.zip!
