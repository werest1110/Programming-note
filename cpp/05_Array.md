# C5 Array
## 5.1 Declaring Array
```cpp
int tests[5];
```

```cpp
const int SIZE = 5;
int tests[SIZE];
```
## 5.2 Store with string
```cpp
char fname[6] = "Henry";
```
|H  | e |n  |r  |y  |\0 |*Total*
|-  |-  |-  |-  |-  |-  |-
|0  |1  |2  |3  |4  |5  |6 space









## Grammar Mistake
```cpp
test[0] = 79;
test[1] = 80;
test[3] = test[0] + test[1];  // test[3] become 159

cout << test;       //not legal
cout << test[3];    //legal (must be individual)
```

```cpp
int

