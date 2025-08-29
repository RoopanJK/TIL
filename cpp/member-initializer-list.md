# Member Initializer List
- Initializer list is used to initialize members of a class.
- The list of members to be initialized are indicated with **constructor** as a comma-separated list followed by a colon.

```
	// Class Initilizer
	MyClass(int i = 0, int j = 0) : x(i), y(j){}
```

- Can also be done as below without `Member Initializer List`


```
	// Class Initilizer
	MyClass(int i = 0, int j = 0)
	{
		x = i;
		y = j;
	}
```