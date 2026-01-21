# C7 Pointer
## 7.1 Getting Address

```cpp
// use &

int x = 5;
cout << "The value of x is " << x << endl;
cout << "The address of x is " << &x << endl;   //using &
```

```cpp
* = "go to the address stored in and look its value"    // (Dereference)
& = "Address of the operator"                           // (Reference)
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
```cpp
void swap(int *x, int *y)   //dereference it to go in address and check the value
{
    int temp = *x;
    *x = *y;
    *y = temp;
}

int main()
{
    int num1=2,num2=-3;

    swap(&num1, &num2);     //call by address

    cout << "1 " << num1 << endl;
    cout << "2 " << num2 << endl;


    return 0;
}
```
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
|**Pointer to Constant**| Yes| No
|**Constant Pointer**| No|Yes
|**Constant Pointer to Constant**|No | No

## 7.8 Dynamic Memory Allocation
### 1) new
- make a valid address with garbage value
```cpp
// Three output address will be different but the output is the reference only
int main()
{
    int *a = new int;
    cout << new int << endl;    //Output = 0x100
    int *b = new int; 
    cout << new int << endl;    //Output = 0x200
    int *c = new int;
    cout << new int << endl;    //Output = 0x300
}

int main()
{
    for (int i=0; i<numDays; i++)
    {
        cout << "Address is " << new int << endl;       //every value[i] the address will be different (each box hold a new valid address with empty value)
        cout << "Enter a value: ";
        cin >> value[i];
    }
}
```
```cpp
//normal variable

int* ptr = new int;  //create a valid address(0x100)
*ptr = 35;
cout << *ptr;       // Output = 35
cout << *new int;   // Output = 0   //create again a valid address(0x200)
```

```cpp
//array (use hotel room and check out scenario)

cout << "Enter number of Day: ";
cin >> numDays;

int *values = new double[numDays]; 
// Here will create a Dynamic memory with numDays size and store in the value pointer 

for (int i; i<numDays ; i++)
{
    cout << "Enter a value: ";
    cin >> value[i];
}
```

### 2) delete
```cpp
//normal variable
int *ptr = new int;
delete ptr;

//array
int *value = new int[numDays];\
delete [] value;
```

## 7.9 Returning Pointers from Functions

```cpp
// Rule 1: must not return a pointer to a **local variable** in function
int* returnLocal() 
{
    int number = 100;    
    return &number;      //number is destroy after out of function
}
```
```cpp
// Rule 2: must return to data that pass as **argument**
int* findLarger(int* a, int* b) 
{
    if (*a > *b) 
        return a;  
    else 
        return b;  
}
int main()
{
    int x = 10, y = 20;
    int* result = findLarger(&x, &y);
}
```
```cpp
// Rule 3: must return to **dynamic memory**
int* createArray(int size) 
{
    int* arr = new int[size]; 
    arr[0] = 50;
    return arr;            
}
int main()
{
    int* myPtr = createArray(5);
    cout << myPtr[0];   // Output = 50
    cout << myPtr[3];   // Output = garbage value
    delete[] myPtr;
}        
```






