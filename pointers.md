# Pointers
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