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

