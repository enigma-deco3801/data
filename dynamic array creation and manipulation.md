### Primary functions
```
malloc()
realloc()
free()
```

___
### Create
```
// Declare and initialise an array to hold one integer.
int *arr;
arr = (int*) malloc(1 * sizeof(int));
```

___
### Add
```
// Reallocate space for the array to store 1 more int
arr = (int*) realloc(arr, ((numElements+1) * sizeof(int)));

// Put the number into the array
arr[numElements] = input;
```

___
### Free
```
// Free memory allocated to store the array
free(arr);
```

___
