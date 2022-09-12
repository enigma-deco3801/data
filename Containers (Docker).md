# Containers (Docker)
___
helloworld.c
```
#include 
int main() { 
	printf ("Hello World\n"); 
	return 0;
}
```

DOCKERFILE
```
FROM scratch 2 
COPY hello-world / 3 
CMD ["/hello-world"]
```

![[Pasted image 20220913003830.png|300]]

![[Pasted image 20220913003843.png|500]]
**Why?**

`ldd` tells us exactly what `hello-world` depends on. The hello world program can be statically compiled so that it does not depend on any libraries.

![[Pasted image 20220913003932.png|500]]



___
### References
[[containers.pdf]]