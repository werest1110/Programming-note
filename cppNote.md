# Pointer
| Data Type          | Function Header       | Function Call | Value Change? |
| ------------------ | --------------------- | ------------- | ------------------ |
| int (value)        | `void f(int x)`       | `f(a)`        | ❌                |
| int (reference)    | `void f(int &x)`      | `f(a)`        | ✅               |
| struct (value)     | `void f(Student s)`   | `f(s1)`       | ❌                |
| struct (reference) | `void f(Student &s)`  | `f(s1)`       | ✅               |
| struct array       | `void f(Student *s)` / `void f(Student s[])`| `f(arr)`      | ✅              |

| Case      | Parameter type           | How to call             | How to access inside |
| --------- | ------------------------ | ----------------------- | -------------------- |
| Pointer   | `const string* filename` | `loadFromFile(&myFile)` | `*filename`          |
| Reference | `const string& filename` | `loadFromFile(myFile)`  | `filename`           |
| Copy      | `const string filename`  | `loadFromFile(myFile)`  | `filename`           |
