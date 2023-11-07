### Syntax
**Common Types**
- Integer
	- 32 bits: `int`
	- 64 bits: `long`
- Floating point
	- 32 bits: `float`
	- 64 bits: `double`
- String
	- 16 bits/char: `string`

**Type Conversion**
- `Convert.ToInt32(): int`
- `Convert.ToDouble(): double`
- `Convert.ToString(): string`

**Variables**
- Immutable
	- `const [type] variableName = value` 
- Mutable
	- `[type] variableName = value`

**MVC Flow interaction**
- Model
- View 
- Controller

**Program entry point**
```
using System;

namespace HelloWorld
{
	class Program
	{
		static void Main(string[] args)
		{
			Console.WriteLine("Hello World");
		}
	}
}
```


**Prints**
- Print without line break
```
Console.Write("Hello")
Console.Write("World")
_____________________________
Hello World
```

- Print with line break
```
Console.Write("Hello")
Console.Write("World")
_____________________________
Hello 
World
```


**User Input**
```
Console.WriteLine("Enter your age: ");
Console.ReadLine();   //input captured in string type
COnsole.WriteLine("Your age is : " + age);
```


### Key components
- Models
	- Typically contains data models, which represents structure of the data entities. These models are used to interact with the application's database, serialize/deserialize data, and define the structure of data exchanged via the API.
	```
	public class Product
	{
		public int Id {get; set;}
		public string Name {get; set;}
		public decimal Price {get; set;}
	}
	```

- Controllers
	- Holds API controller classes. Controllers handle incoming HTTP requests, process them, and return appropriate responses. These classes define the endpoints of your API and the actions (methods) associated with each endpoint. Each action corresponds to an HTTP method (GET, POST, etc. ) and defines how your API handles requests and produces response
	```
	[ApiController]
	[Route("controller")]
	public class ProductController : ControllerBase
	{
		[HttpPost]
		public IActionResult CreateProduct(Product product)
		{
			// logic to create new product
		}

		[HttpGet]
		public IActionResult GetProduct()
		{
			// logic to retrieve product
		}
	}
	```

- `Program.cs`
	- The `Program.cs` file is the entry point of the application. It typically contains the Main method, which is the starting point for the application's execution. 

- `appsettings.json`
	- The `appsettings.json` file contains configuration settings for the application. These settings can include things like database connection strings, logging configurations, API keys, and other application-specific settings. The settings in this file can be accessed throughout your application to configure various aspects.

- `Properties/launchSettings.json`
	- It is used for configuring how your application is launched for debugging or running locally. It specifies settings such as the hosting environment, application URL, and other runtime options. This file can be used to define multiple profiles with different settings for different development scenarios.

### EF Core Commands
**Add Migration**
```
Using Package Manager Console in Visual Studio:
Add-Migration <MigrationName>

Using .NET CLI:
dotnet ef migrations add <MigrationName>
```

**Update**
```
Using PMC in VS:
Update-Database

Using .NET CLI:
dotnet ef database update
```

**Roll Back Migration**
```
Using PMC in VS:
Update-Database <TargetMigration>

Using .NET CLI:
dotnet ef database update <TargetMigration>
```

**Remove Migration**
```
Using PMC in VS:
Remove-Migration

Using .NET CLI:
dotnet ef migrations remove
```


### Create API
**Add a new model**
- On the project, add a new folder Models.
- In the new folder Models, add a new class (*.cs).

