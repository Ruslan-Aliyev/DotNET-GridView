# GridView .NET

Nested GridViews as FrontEnd and EntityFramework as BackEnd</h3>
					
## In Employees table 'ID' is the primary key & 'DepartmentId' is the foreign key. The general setup in the BackEnd should be like this:

![](https://raw.githubusercontent.com/atabegruslan/DotNET-GridView/master/Illustrations/gv1.PNG)

## The general setup in the FrontEndEnd should be like this:

![](https://raw.githubusercontent.com/atabegruslan/DotNET-GridView/master/Illustrations/gv3.PNG)

## The result should be like this:

![](https://raw.githubusercontent.com/atabegruslan/DotNET-GridView/master/Illustrations/gv2.PNG)

## Steps:

1. Set up the 2 tables in SQL Server Management Studio
2. In Visual Studio: New ASP.NET Web Application
3. Use NuGet to install EntityFramework
4. Solution Explorer: Right click project, new item, under the 'Visual C# - Data section' select 'ADO.NET Entity Data Model', name it EmployeeModel.edmx, add, 	
5. Continuing through the Database connection wizard: Select 'Generate from Database', next, click 'new connection' and specify data source, server name, DB login credentials & name of the database, test connection, ok, 
6. Continuing through this same wizard: Save entity connection settings in Web.Config as 'EmployeeDBContext', next, VS will now create a EmployeeDBContext file AND try to connect to the back end, 
7.  this wizard loads the back-end, select the Departments and Employees tables, Model namespace is EmployeeModel, finish.
8. Add new WebForm item to project.
9.  View-Toolbox-GridView and View-Toolbox-EntityDataSource into the form part of the WebForm aspx code.
10. Compile project.
11. Configure EntityDataSource's Data Source, wizard pops up, in the named connection drop menu select EmployeeDBContext, next, select Departments from the EntitySetName drop menu, tick 'select all (entity value)'.
12. Configure the GridView, in the Chose Data Source menu chose the name of the EntityDataSource that you just configured.
13. Configure the GridView, edit columns, add a template field, Header Text is 'Employees', finish.
14.  the GridView, edit templates, drag in another View-Toolbox-GridView into the ItemTemplate.
15. Edit the data bindings of that inner GridView, wizard pops up, select 'custom bindings', Code Expression is 'Eval("Employees")', ok.
16. Go back to the outer GridView and end template editing.
17. Select the EntityDataSource, go to its properties, "include: Employees".
18. Configure outer GridView, edit templates, and you enter the inner GridView, Configure the inner GridView, EditColumns, add 3 bound fields (Header Texts: 'First Name', 'Last Name', 'Gender' ; DataField: 'FirstName' , 'LastName', 'Gender' respectively ), ok.
19. Select inner GridView, go to its properties, false for Auto Generate Columns.
