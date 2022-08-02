# Struct
___
### [[typedef]]

___
### Initialize

**Without pointer**
```
MyStruct obj;

obj.a = 8;
obj.b = "hello";
```

**With pointer**
```
MyStruct* obj;
obj = malloc(sizeof(MyStruct));

obj->a = 8;
obj->b = "hello";
```

___
