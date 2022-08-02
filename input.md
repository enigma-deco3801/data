### Taking input in loop
```
char buffer[80];
char* line;

// this is equivalent to "while fgets doesn't return NULL"
while ((line = fgets(buffer, 80, stdin))) {
	
}
```