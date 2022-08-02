# Pointers
___
### Pointer Basics
```
// creating an empty pointer
int *x;

// allocating the pointer (to empty)
x = (int*) malloc(1 * sizeof(int));

// or allocating to existing variable
int a = 10;
x = &a;
printf("%i", *x); // 10
```

___
[[dynamic array creation and manipulation]] using pointers

___
### Pointers Visualization
![[pointers 2022-08-01 16.14.33.excalidraw]]

___
### Program to see how pointers work for yourself
```
#include <stdio.h>

int main() {
    int a = 10;
    int *x = &a;
    int *y = x;
    int **z = &x;

    printf("values: %i %i %i %i\n", a, *x, *y, **z);
    printf("memory: %i %i %i\n", &a, x, y, *z);
    printf("memory: %i %i %i\n", &x, &y, z);
    printf("memory: %i\n", &z);
}
```

___
### Incrementing over a `char*` pointer
```
char* str = "hello";

// Way 1
int i = 0;
while(str[i]) {
	// do whatever
	i++;
}

// Way 2
char* ptr = str
while(*ptr) {
	// do something
	ptr++;
}
```

___
### Usage in [[structs]]
```
MyStruct* obj;
obj = malloc(sizeof(MyStruct));

obj->a = 8;
obj->b = "hello";
```