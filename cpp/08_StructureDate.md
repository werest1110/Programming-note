# C8 Structure Data
## 8.1 Combining Data into Structure
- *struct* does not **allocate memory** and **create variable**!!!
```cpp
struct Student  //Begin with uppercase letter.
{
    int studentId;
    string name;
    double gpa;
};  //remember to put;
```

To declare
```cpp
Student a;
```

## 8.2 Access Structure
1)  use dot (.)
```cpp
Student a;

cin >> a.studentId;
getline(cin, a.name);
a.gpa = 4.00;
```
2) comparing using dot also!!!
```cpp
if (a.gpa == b.gpa)
{
    .....
}
```


## 8.3 Initializing a Structure
 ```cpp
Student a = {123, "Willam", 4.00};
 ```

## 8.4 Array of Structure
- Define Struct in Array
```cpp
struct Student  //Here the struct
{
    int studentId;
    double gpa;
}
```
```cpp
const int SIZE =5;
Student namelist[SIZE];     //Here declared
```

```cpp
cout << namelist[4].gpa;    //Here cout
```

## 8.5 Nested Structure
```cpp
struct PersonalInfo
{
    string names,city;
}

struct Student
{
    int studentId;
    PersonalInfo a;     //take note for this 'a'
}
```

```cpp
Student s;
s.gpa = 4.0;            //Here the outside struct
s.a.names = "Werest";   //Here entered inside struct using 2 dot
s.a.city = "KL";

```

## 8.6 Structure as a Function Argument
### 1) Pass by value
```cpp
struct Student
{
    int studentId;
    double gpa;
};

void showResult(Student s)
{
    cout << "Here the result: " << endl;
    cout << "ID: ";
    cout << s.studentId << endl;
    cout << "Result: ";
    cout << s.gpa << endl;
}

int main()
{
    Student ya;
    cout << "Enter student id: ";
    cin >> ya.studentId;
    cout << "Enter result: ";
    cin >> ya.gpa;

    showResult(ya);

    return 0;
}
```
```cpp
//Pass the struct
showResult(ya);

//Pass the struct variable
showResult(ya.gpa);
```

### 2) Pass by Reference
```cpp
void showResult( Student &s);

// (& Student s) Not Work !!!
// (Student &s) Work !!!
```

## 8.7 Returning a Structure from function
```cpp
//Struct data
struct Circle
{
    double radius;
    double diameter;
    double area;
};

//Prototype
Circle getInfo();

int main()
{
    Circle c;
    c = getInfo();  //Function call
}

Circle getInfo()
{
    Circle a;                       //create a temporary variable
    cout << "Enter radius: ";
    cin >> a.radius;

    return a;                       //return temporary variable
}
```

## 8.8 Pointer to Structure
- A structure data has an address
```cpp
// Pointer it
Student *a;

//Assign address
a = &stu1;

//Access using ()
cout << "Enter ID: ";
cin >> (*a).student ID;
cout << (*a).student ID;
```

```cpp
struct Student
{
    string name;
    double gpa;
};

void getData (Student *s)
{
    cout << "Student name: ";
    getline(cin, (*s).name);
    
    cout << "Current GPA: ";
    cin >> (*s).gpa;
}

int main()
{
    Student ya;
    Student *stu1;
    stu1 = &ya;

    getData(stu1);

    cout << (*stu1).name << endl;
    cout << (*stu1).gpa;

    return 0;
}
```



## Grammar mistake
```cpp
Student a;
cout << a;      //wont work
cout << a.gpa;  //work
```