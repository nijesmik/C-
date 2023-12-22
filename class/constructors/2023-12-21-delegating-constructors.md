> **출처** <br>
> 📚 [Professional C++ 3rd Edition](https://www.amazon.com/Professional-C-Marc-Gregoire/dp/1118858050)

# Delegating Constructors (위임 생성자)

**Delegating constructors** allow constructors to call another constructor from the same class. However, this call cannot be placed in the constructor body; it must be in the constructor initializer and it must be the only member-initializer in the list. Following is an example:

```c++
SpreadsheetCell::SpreadsheetCell(const std::string& initialValue)
    : SpreadsheetCell(stringToDouble(initialValue)) {}
```

When this `string` constructor (the delegating constructor) is called, it will first delegate the call to the target, `double` constructor. When the target constructor returns, the body of the delegating constructor will be executed.

Make sure you avoid constructor recursion while using delegate constructors. For example:

```c++
class MyClass {
    MyClass(char c) : MyClass(1.2) {}
    MyClass(double d) : MyClass('m') {}
};
```

The first constructor will delegate to the second constructor, which delegates back to the first one. The behavior of such code is undefined by the standard and depends on the compiler.
