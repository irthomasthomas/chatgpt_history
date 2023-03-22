## USER
If you make it a policy to use forward declares as much as possible. Not only will a project consisting of lots of .cpp file compile faster, but you almost never have to worry about circular dependencies. Basically, if you don't need the full definition in the header, use a forward declare

## ASSISTANT
Using forward declarations can indeed help reduce compilation times, especially in large projects with many dependencies. It can also help reduce the risk of circular dependencies, as you mentioned.

A forward declaration is a way to tell the compiler that a particular identifier refers to a type or a variable that has been defined elsewhere, without providing the full definition. This allows you to use the identifier in a limited way, such as declaring a function that takes a pointer or reference to the type, without having to include the full definition of the type in the header file.

For example, if you have a class `Foo` and another class `Bar` that has a member of type `Foo`, you could use a forward declaration for `Foo` in the header for `Bar`:

```
// In Bar.h
class Foo;

class Bar
{
    Foo* foo;
};
```

This would allow you to use `Foo*` in the declaration of `Bar`, without including the full definition of `Foo` in the header. The full definition of `Foo` would still need to be included in a source file, however, when you actually create an instance of `Foo` or call any of its member functions.

There are a few limitations to using forward declarations. For example, you cannot create an instance of the type or call its member functions using a forward declaration. You also cannot take the size of the type, or define any functions or variables that use the type as a parameter or return type. In these cases, you will need to include the full definition of the type in the header.

Overall, using forward declarations can be a useful technique for optimizing compilation times and reducing dependencies in C++ projects, but it's important to understand the limitations and use them appropriately.