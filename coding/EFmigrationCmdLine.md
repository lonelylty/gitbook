```
get-help entityframeworkcore

code first

Add-Migration Migration-FileName -c DBContext

Update-Database -c DBContext  #update-database -verbose  script-migration


dbfirst

--sqlserver
Scaffold-DbContext -Connection 'connectString' -Provider Microsoft.EntityFrameworkCore.SqlServer -OutputDir DirName -ContextDir DirName -Context NameContext
 -Tables tablename1,tablename2,...

--mysql
Scaffold-DbContext -Connection 'connectString' -Provider Pomelo.EntityFrameworkCore.MySql -OutputDir DirName -ContextDir DirName -Context NameContext
 -Tables tablename1,tablename2,...

```