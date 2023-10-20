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