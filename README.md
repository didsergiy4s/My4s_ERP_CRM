# My4S

**My4S** – a constructor program for building web applications (ERP, CRM, etc).
- It is a freely distributed web application with open-source code.

- **Server side:** Node.js (currently Windows only)  
- **Database:** Firebird 3+  
- **Administration:** Firebird Editor Pro  

My4S can be a great tool for small and medium-sized businesses, especially if you need a flexible and free ERP/CRM system.

---

## Features

1. **Finance and Accounting Management**  
   Configure registers for tracking income, expenses, and taxes.  
   Built-in balance sheets for budget analysis.

2. **Inventory Management**  
   Track goods, monitor stock levels, automate purchasing, and analyze sales.

3. **Customer and Sales Management**  
   Manage directories of contractors, document flow, automate invoicing, and analyze sales.

4. **Business Process Automation**  
   Create documents and registers to automate key processes — from payroll to task planning.

5. **Flexible Customization**  
   Add new modules and functions, expand reporting, and integrate with other services.
   
Overall, My4S is a ready-made startup that lacks only one thing: for someone to believe in the program.

Now I can clearly outline the system portrait for those looking for a solution:
Full accounting cycle: From a simple customer list (CRM) to complex warehouse (balance registers) and financial operations (accounting accounts).
Ready Frontend + Backend: No need to design the Firebird database structure from scratch - the basic entities (directories, balance registers, information registers, documents) are already working.
Zero Cost: Powerful Enterprise-level tool, available as a free startup

Why it's perfect for a beginner developer or startup:
Minimal "Time to Market": Instead of spending half a year designing tables and relationships for double-entry in SQL, a developer can deploy My4s and
in a week give the client a prototype that can already calculate balances and show the balance.
Freedom of choice: You don't impose exactly what the business process should look like. One person will create a system for a pharmacy on your database, another for accounting for auto parts,
and the third for managing a small charitable foundation.
Low cost of error: Since the database is already ready and tested, the risk of making an error in balance calculations or accounting entries is minimal.

My4s is a specialized tool for developers that combines the properties of a framework and a Frontend designer. Unlike ready-made static programs,
this project is created as a flexible framework for building business automation systems.
Here are the key characteristics of the project:
1. Purpose and scope
   The project is focused on creating complex corporate solutions:
   ERP systems: Enterprise resource management.
   CRM systems: Customer and sales management.
   Accounting systems: Accounting and warehouse automation.
2. Technology stack
   My4s is based on proven technologies that ensure fast work with data:
   Node.js: Used as an execution environment for the server part.
   Firebird SQL: A reliable relational database that is often chosen for its stability and ease of administration in accounting systems.
   JavaScript: The main development language.
3. Project philosophy
   The main idea of ​​My4s is flexibility. This is not a "boxed" solution where the user is limited to the developer's functionality, namely the designer. It allows you to:
   Quickly create interfaces (Frontend) for specific business tasks.
   Scale the system depending on the needs of the project.
   Use open source code for free distribution and improvement by the community.
4. Accessibility
   The project is distributed as Open Source (open source software). Its distributions and source code can be found on GitHub, which makes it available
   to other programmers looking for a free and reliable base for their developments.
   This is a tool for those who want to have full control over the architecture of their accounting system without spending time writing basic interface elements from scratch.

## My4S features

After the release of Firebird 3.0 and higher, the restrictions on the size of the database (up to 128 Tb) and tables (up to 64 Tb) were significantly increased.
In fact, now everything depends only on the capabilities of the server.
In this regard, I decided to make only one table for documents, directories, information registers and others.
For the sake of understanding, let's consider only one table for now - directories (CATS). But how can each table accommodate dozens, or maybe hundreds of different directories of the type
nomenclature, contractors, etc.? Each table has standard columns (id, id_n, name, actual, cod ...), and for the remaining columns we will use the blob(memo) field.
And all other fields (columns), unique for each directory, we will write in a JSON-type string. I think experienced programmers have already understood my idea.
NoSQL has been around for a long time, and it is no wonder that reputable databases have begun to implement JSON.

                                Browser forms
Each table (directories, documents, information registers, and others) will have a single HTML code template with fixed standard data,
as well as a single-row HTML table template. Two tables are provided for documents: one for the document header (with one row),
the other for the tabular part (multi-row). This design eliminates the need for a form editor (IDE); it is enough to use a good
HTML code editor (for example, Visual Studio Code).
Before opening the form, the template will be dynamically updated for each specific metadata object, using data stored in blob fields or JS files.

                                Database optimization
The program is designed to minimize database access. Everything created in the Designer is described by the properties of each metadata
and written to the blob of the table field. At the same time, this data is saved in a special JS file associated with a specific metadata.
When opening the metadata form, the data is not loaded from the database, but is connected via the SRC JS file. This file is updated with each change in metadata in the Designer.
Such preparatory JS files significantly reduce database access, since the program works with pre-loaded data.

The program supports:
• balance registers (simple and accounting, including a reference book of accounting accounts);
• write-off of cost using the average method (I have not yet described Fifo and Lifo - you can add them yourself);
• ready-made turnover and balance information for both balance registers and accounting registers (with selections and saving settings);
• up to seven multi-line tables in one document.

                                Database recovery mechanism
I have developed and successfully tested a database recovery mechanism after a critical failure. Its essence is to restore the database exactly to the moment of failure.
Recovery process:
1. After creating a database backup archive, logging of all UPDATE and INSERT operations begins.
2. All SQL UPDATE and INSERT blocks that are passed to the Firebird driver are written to files inside the logs folder for each database separately, if you have several databases on your computer.
3. In case of a failure, the database is restored from the last backup archive.
4. Then, all saved files in the logs folder are processed in a loop and passed to Firebird for execution, thus restoring even the changes made in the Designer!
   Attention! So far, I have not inserted this mechanism into My4s. But in the logs folders there is a bec_res folder in which the necessary files are located,
   with the help of which you can restore the database.
   In these files, you must correctly specify the paths as on your server and also correctly specify the password. THIS will be possible only for experienced programmers.

                                Working with different time zones
It is now possible to work with clients in the database while being in different time zones.
Clients can be located in different countries or in one large country with several time zones.
How to store dates on the server?
We do this, the server, no matter what time zone it is in, is always tied to the zero zone of London (winter only!).
And for each client we always calculate the offset relative to London (timezoneOffset)
and when recording dates on the server we adjust the client's date to this Offset.
When receiving reports by date, again using Offset, we receive a report in the client's time zone!
By default, the program is configured to work in one time zone. In the Blob.js module, at the beginning, there is a variable: "let timezoneOffset = 0;". If you set this variable to 1,
then the program with different zones will start working!

                                Let's summarize what was written above.
I understand that in some places the description may not be completely clear right away.
But this description is enough for you to decide whether you want to continue exploring My4s or not. First, read the Help carefully.
There are a lot of screens there. If you want to continue, then you first need to install the demo version and go through the description using specific examples.
Then many things will become clearer.

I express my deep gratitude to the developers of Node.js, Firebird databases, Firebird Editor Pro, Visual Studio Code!


## Documentation

- ߓĠ[Help4s_en.pdf](Help4s_en.pdf) — English description  
- ߓĠ[Help4s_ua.pdf](Help4s_ua.pdf) — Ukrainian description  

⚙️ The file `Distrib_My4s.zip` (available in [Releases](../../releases)) contains everything needed to build the program.  
Follow the instructions in the Help file.

---

## Contact

  Author: sergey2429@i.ua  

---

## ߒ֠Support
If this project helped you, please consider supporting it:
* **PayPal:** [Donate via PayPal](https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=sergey2429@i.ua&currency_code=USD)

* Для украины в гривнях карточка Ощад банка : 5167 8032 1042 4912

---

## License

MIT License — see the [LICENSE](LICENSE.md) file.
