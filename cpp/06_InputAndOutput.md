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
### 4. Priority for Output
```
1. fixed
2. setprecision
3. showpoint
4. left
5. right
6. setw
```

## 6.2 Formatting Input
### 1. getline()
```cpp
//Store in char
const int SIZE = 20;
char name[SIZE];

cout << "Enter your name: ";
cin.getline(name,SIZE);

----------------------------------------------------------
//Store in string
string name;

cout << "Enter your name: ";
getline(cin, name);
```

### 2. get()
```cpp
char ch;
cout << "Enter whitespace: ";
cin >> ch;                      //continue asking until a character to be read

char ch;
cout << "Enter whitespace: ";
cin.get(ch);                    //read any key including the whitespace.
```

### 3. ignore()
```cpp
cin.ignore();
cin.ignore(10, '\n');

//use after cin >>
```

## 6.3 File Operation
**Output file** means the file out from my hand *(can edit)*
**Input file** means the file come in my hand *(can read only)*

```cpp
//library
#include <ifstream>      //input file
#include <ofstream>      //output file
#include <fstream>       //both input and output (normally put this)

//declare
ofstream outfile;
ifstream infile;         

//then baru boleh open file
```

### 1. Opening File
```cpp
//ifstream and ofstream
infile.open("haha.txt");
outfile.open("haha.txt");

//fstream
infile.open("haha.txt", ios::in);
outfile.open("haha.txt", ios::out);

dfile.open("haha.txt", ios::in | ios:: out); //combine
```
**Testing the file Open**
```cpp
//1.
if (!input)
{
    cout << "Error";
}

//2.
if (input.fail())
{
    cout << "Error";
}

//3.
if (!input.is_open())
{
    cout << "Error";
}
```

### 2. Using File
```cpp
outfile << "haha.txt";  //send data into haha file

infile >> "haha.txt";   //copy data from haha file
```

### 3. Closing File
```cpp
infile.close();
outfile.close();
```
