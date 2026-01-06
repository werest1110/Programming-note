# C7 Pointer
## 7.1 Getting Address

```cpp
// use &

int x = 5;
cout << "The value of x is " << x << endl;
cout << "The address of x is " << &x << endl;   //using &
```

```cpp
* = "go to the address stored in and look its value"
& = "Address of the operator"
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
![](/images/image.png)

## 7.6 Comparing Pointer
```cpp
//Compare value 
if (*ptr1 == *ptr2)

//Compare address
if (ptr1 == ptr2)
```

## 7.7 Pointers as Function Parameters
### 1) Pointer to Constant
If a data using **const** means that the value can't be change. Hence, if we gonna to **store it in a pointer** we have to use **Pointer-to-const**.
```cpp
const int SIZE = 6;
const double payRates[SIZE] = { 18.55, 17.45, 12.85, 14.97, 10.35, 18.89}
// Here the values(18.55,17.45...) and the SIZE of array is locked
```

#### Declaring
```cpp
double *ptr = payRates;             // Wrong
const double *ptr = payRates;       // True
```

- In this array, we can only **change the address** of pointer to see what value inside **instead of change value**.

Ex.
```cpp
cout << *ptr;       // Output = 18.55
ptr ++;           
cout << *ptr;       // Output = 17.45
```
### 2) Constant Pointer
A pointer that **cannot change address** after initialized but **change only the value**.
```cpp
int *const ptr;
```

```cpp
int num1 = 22;
int num2 = 50;
int *const ptr = &num1; //Initialized

*ptr = 30;          // True
ptr = &num2;       // False
```

### 3) Constant Pointer to Constant (combine)
- Rule 1 : **Cannot change the data** pointed to
- Rule 2 : **Cannot change the address** pointed to
- Rule 3 : Read from **right to left**

```cpp
//Rule 3
const int *const ptr = &value; // ptr is a constant pointer that point to const int value
```

```cpp
int value = 22;
int extra = 50;
const int * const ptr = &value;

*ptr = 30;              // Error
ptr = &extra;           // Error
```
### 4) Summary

|Type|Can change address? | Can change data?
|:-: |:-: | :-:
|**Regular**|Yes | Yes
|**Pointer to Constant**| No| Yes 
|**Constant Pointer**| Yes|No
|**Constant Pointer to Constant**|No | No






