# BASE-WEBAPI PROJECT
Base project to create a webapi netcore

Folder Structure:
* Controllers
* Core
  * Helper
  * Interfaces
  * Mapper
  * Models
  * Services
* DataAccess
  * Entities
  * Repositories
  * Interfaces

## To use this template:

At program.cs:
- Add services to container after line "// Add services to the container."
- Add repositories to services after lines "// Add repositories to services"

Documentation
The project enabled documentation on file webapiProject.csproj with the node:
<Project>
  <PropertyGroup>
    <GenerateDocumentationFile>True</GenerateDocumentationFile>
  </PropertyGroup>
</Project>
Will generates warning on definitions without documentation.

## Libraries to use:
### Automapper
program.cs:
  This lines uses injection for automapper
  builder.Services.AddAutoMapper(AppDomain.CurrentDomain.GetAssemblies());
Core.Mapper.EntityMapper.cs:
  Includes configuration to map between entities and models.

### Swagger. 
Enables api documentation

program.cs:

builder.Services.AddSwaggerGen(c =>
{
    //The generated Swagger JSON file will have these properties.
    //Update Api info:
    c.SwaggerDoc("v1", new OpenApiInfo
    {
        Title = "Your Api Name",
        Version = "v1",
        Description = "Your Api Description.",
        TermsOfService = new Uri("http://www.yourUrl.com/TermsOfService"),
        Contact = new OpenApiContact
        { Name = "Contact Title", Email = "contactemailaddress@domain.com", Url = new Uri("http://www.yourUrl.com") }
    });


    //Locate the XML file being generated by ASP.NET...
    var xmlFile = $"{Assembly.GetExecutingAssembly().GetName().Name}.XML";
    var xmlPath = Path.Combine(AppContext.BaseDirectory, xmlFile);
    //... and tell Swagger to use those XML comments.
    c.IncludeXmlComments(xmlPath);    //You can remove this line if you want to hide the documentation
});




