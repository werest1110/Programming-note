# C7 Pointer
## 7.1 Getting Address

```cpp
// use &

int x = 5;
cout << "The value of x is " << x << endl;
cout << "The address of x is " << &x << endl;
```

## 7.2 Pointer Variable
![](/images/ptr.png)

```cpp
int x =5,y=6;
int *ptr;   //now we deaclare the variable

ptr = &x;   //now the ptr point at x and store address
*ptr = y    //now thw ptr value change only means that x equal to y but the ptr still pointed at x;
```

*Example* (must know how to draw)
![](/images/ptr1.png)

## 7.3 Relationship btw array and pointer

```cpp
// 1. Array name as pointer
int val[4] = {1,2,3,4};

int *val;                   //auto set at val[0]
cout << *val << endl;       //Output = 1
---------------------------------------------------------
// 2. Pointer act as the array
int val[4] = {1,2,3,4};

int *valptr = val;
cout << *valptr << endl;    //Output = 1
cout << valptr[2] << endl;  //Output = 3
---------------------------------------------------------
// 3. Output for ptr and *ptr
int val[4] = {1,2,3,4};
int *valptr = val;

cout << valptr << endl;    //Here cout the address
cout << *valptr;           //Here cout 1
```

## 7.4 Pointers Arithmetic
```cpp
int vals[] = {4,7,11};
int *valptr = vals;
```

```cpp
// ++, -- 
valptr ++;  
cout << *valptr << endl;        // Output = 7

// +,-
cout << *(valptr+2) << endl;    // Output = 11

// +=,-= 
valptr +=2;
cout << *valptr << endl;        // Output = 11

//-
cout << valptr - val; << endl;  
```

|Operation|Action | What happen|Example
|:-:|:-:|:-:|:-:
|++/--| Step by step | Ptr change **permanently**|valptr++
|+,-|Jump|Ptr does not change |*(valptr+2)
|+=,-=| Jump|Ptr change **permanently** | valptr+=2

## 7.5 Initializing Pointers





