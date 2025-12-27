# C6 Input and Output
## 6.1 Formatting Output
### 1. setw(n)
```cpp
//right justified
cout << setw(6) << "Hello";         //Output: XHello
cout << setw(4) << "Hello";         //Output: Hello (cuz the n is less than the string size.)
```
```cpp

int x = 15;

//with left
cout << left;
cout << setw(4) << x << endl;       //Output: 15XX

//with right
cout << right;
cout << setw(4) << x << endl;       //Output: XX15
```

### 2. fixed and showpoint
fixed       : 6 decimal point (for int also)
showpoint   : 6 significant digit

```cpp
//combination
double x = 15.674;

cout << fixed << showpoint; //fixed higher priority than showpoint
cout << x;     //Output: 15.674000
```

### 3. setprecision(n)
```cpp
//without fixed
double x = 156.74;
cout << setprecision(3) << x << endl;   //157
cout << setprecision(2) << x << endl;   //1.6e+01

//with fixed
double x = 156.74;
cout << fixed << setprecision(1) << x << endl;  //156.7
```