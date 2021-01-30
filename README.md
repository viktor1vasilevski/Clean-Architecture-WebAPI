# Clean-Architecture-WebAPI

This is a WebAPI, implemented with Clean Architecture pattern. The code is very clean and it is very manageable. 
You can add your own models, validations, etc, and you can actually create MVC project on top of it, or just 
use it as a api, deployed locally or publish on some server and use some front-end framework to show the data.

There are some steps that you have to do, to get working on you computer:

1.  Change the connection string - In the WebAPI project in the appsettings.json file enter your server name 
    and name of the database(I was working on SQL Server 2014 Management Studio).

2.  Go into the Package Manager Console and type: add-migration 
    !IMPORTANT - Make sure that your WebAPI is Set as Startup Project, 
    and in the Package Manager Console your Default project is CleanArchitectureWebAPI.Infrastructure.Data selected.
    
    - this will create folder Migration in CleanArchitectureWebAPI.Infrastructure.Data with the migrations. 
      This will create the Migration with all the ASP.NET tables and models.
      
3.  When this is done just type in the Package Manager Console: update-database.
    - This will create the database with you database name with all the ASP.NET Identity tables and the models.
    - In the WebAPI project it will also be created folder Log with two files. One .json file and other .txt.
      These are for detail logging information.
    
    Because the API works with roles "Admin" and "User", you have to go first to create roles "Admin" and "User" in dbo.AspNetRoles 
    with some number Id. (because "User" is with Id 2(this is set to be automatically), make "Admin" with Id 1).
    
4.  Next step is to get registered - automatically this user will have the role "User". 
    Go in the table AspNetUserRoles and notice that the RoleId is already 2 for that one user. Just change it manually to 1 and press TAB. 
    This user, from then on will be with the role of "Admin". 
    
    Every other registered user in the future will be with the role "User". To change it to "Admin" just do the previous step. 
    (in the project there is no request that is authorized by "User", so you can use this:
      [Authorize(AuthenticationSchemes = JwtBearerDefaults.AuthenticationScheme, Roles = "User")] <<<, below some other Http request).

This WebAPI uses JSON Web Token (JWT) for Authorization and Information Exchange.
This WebAPI also uses swagger, so you can test it. Just write in the URL insted of {url}/api/soaps, or {url}/api/balms, just write {url}/swagger.
This WebAPI uses Serilog for activity tracking.

Then just run the project on F5 and this will build the project and it will seed the database with some data, just something to work with. (maybe you have to close the SQL Server 2014 Management Studio and start it again)
So the project is very useful because it show how to implement Clean Architecture Design, Domain-Driven Design, Separation of Concerns, Basis of OOP, Validation and User Authentication and Authorization, Token, AutoMapper, Inversion Of Control, SOLID Principles and more.

I like to mention one tiny mestake - the name Domian is wrong. It should be Domain, not Domian.
At the very end I notice that mestake when everything was done. So I hope it doesn't bother anyone.

Happy Coding :)
