## Table of Contents

- [BBD Group 3 C# Style Guide](#BBD-Group-3-C#-Style-Guide)
  - [Inspiration](#inspiration)
  - [Nomenclature](#nomenclature)
    - [Namespaces](#namespaces)
    - [Classes & Interfaces](#classes--interfaces)
    - [Methods](#methods)
    - [Fields](#fields)
    - [Properties](#properties)
    - [Parameters](#parameters)
    - [Actions](#actions)
    - [Misc](#misc)
  - [Declarations](#declarations)
    - [Access Level Modifiers](#access-level-modifiers)
    - [Fields & Variables](#fields--variables)
    - [Classes](#classes)
    - [Interfaces](#interfaces)
  - [Spacing](#spacing)
    - [Indentation](#indentation)
      - [Blocks](#blocks)
      - [Line Wraps](#line-wraps)
    - [Vertical Spacing](#vertical-spacing)
  - [Brace Style](#brace-style)
  - [Switch Statements](#switch-statements)
  - [Language](#language)
  
# BBD Group 3 C# Style Guide

This style guide is adapted from [The Official kodeco.com C# Style Guide](https://github.com/kodecocodes/c-sharp-style-guide) to keep the code in our projects consistent.  

Our overarching goals are **conciseness**, **readability** and **simplicity**.  

## Inspiration

This style guide is based on C# conventions.

## Nomenclature

On the whole, naming should follow C# standards.

### Namespaces

Namespaces are all **PascalCase**, multiple words concatenated together, without hyphens ( - ) or underscores ( \_ ). 

Exception to this rule are acronyms like GUI or HUD, which can be uppercase.

### Classes & Interfaces

Classes and interfaces are written in **PascalCase**. For example `RadialSlider`.

All Interface class names must be prefixed with a capital 'I', e.g. `IEmployee, IAnimal`

Each Class should represent a singular object and perform a single purpose


### Methods

Methods are written in **PascalCase**. For example `DoSomething()`. 

The method signature should not contain a space between the name and the parenthesis e.g: `Foo()` NOT `Foo ()`

Method names should try to best describe the purpose of the method

Methods should not perform more than one function at a time

```csharp
public int AddTwoNumbers(int one, int two)
{
  return one + two;
}
```
**AVOID:**

```csharp
public int AddTwoNumbers(int one, int two)
{
  return one + two;
  x = DoSomeExtraCalculations();
}

### Fields

All fields that are non-static should be written in **camelCase**.

For example:

```csharp
public class MyClass 
{
    public int publicField;
    int packagePrivate;
    private int myPrivate;
    protected int myProtected;
}
```

**AVOID:**

```csharp
private int _myPrivateVariable
```

**PREFER:**

```csharp
private int myPrivateVariable
```

Static fields are the exception and should be written in **PascalCase**:

```csharp
public static int TheAnswer = 42;
```

All constants should be in **ALL CAPS**

Names of fields should be used to describe the data that they contain.
**Exception:*
```For iterable variables in loops (int i = 0)```

Fields should not be prefixed with any non-standardised naming e.g. int sp_Students()

It needs to be ensured that variables that include types, should be platform agnostic, i.e. int intSum. Should the variable require the data type in its name, refer to computer-based specifications e.g. int int32Sum (More important for comments).

### Properties

All properties are written in **PascalCase**. For example:

```csharp
public int PageNumber 
{
    get { return pageNumber; }
    set { pageNumber = value; }
}
```

When more control is wanted, avoid built-in get and set, use possible custom gets and sets.

Only use get or set when needed, never use unnecessary abstraction.

### Parameters

Parameters are written in **camelCase**.

**AVOID:**

```csharp
void DoSomething(Vector3 Location)
```

**PREFER:**

```csharp
void DoSomething(Vector3 location)
```

Single character values are to be avoided except for temporary looping variables.

### Actions

Actions are written in **PascalCase**. For example:

```csharp
public event Action<int> ValueChanged;
```

### Misc

In code, acronyms should be treated as words. For example:

**AVOID:**

```csharp
XMLHTTPRequest
String URL
findPostByID
```  

**PREFER:**

```csharp
XmlHttpRequest
String url
findPostById
```

Only use world standardised abbreviations, no custom ones.

No spaces between any operation and its immediate opening bracket.

**AVOID:**

```csharp
for ()
while ()
```  
**PREFER:**

```csharp
for()
while()
```

There should be spaces between all operators.

**AVOID:**

```csharp
counter=3+5;
```  

**PREFER:**

```csharp
counter = 3 + 5;
```

## Declarations

### Access Level Modifiers

Access level modifiers should be explicitly defined for classes, methods and member variables.

### Fields & Variables

Prefer single declaration per line.

**AVOID:**

```csharp
string username, twitterHandle;
```

**PREFER:**

```csharp
string username;
string twitterHandle;
```

### Classes

Exactly one class per source file, although inner classes are encouraged where scoping appropriate.

### Interfaces

All interfaces should be prefaced with the letter **I**. 

**AVOID:**

```csharp
RadialSlider
```

**PREFER:**

```csharp
IRadialSlider
```

## Spacing
 

### Indentation

Indentation should be done using **spaces** — never tabs.  

#### Blocks

Indentation for blocks uses **4 spaces** for optimal readability:

**AVOID:**

```csharp
for (int i = 0; i < 10; i++) 
{
  Debug.Log("index=" + i);
}
```

**PREFER:**

```csharp
for (int i = 0; i < 10; i++) 
{
    Debug.Log("index=" + i);
}
```

#### Line Wraps

Indentation for line wraps should use **4 spaces** (not the default 8):

**AVOID:**

```csharp
CoolUiWidget widget =
        someIncrediblyLongExpression(that, reallyWouldNotFit, on, aSingle, line);
```

**PREFER:**

```csharp
CoolUiWidget widget =
    someIncrediblyLongExpression(that, reallyWouldNotFit, on, aSingle, line);
```

### Vertical Spacing

There should be exactly one blank line between methods to aid in visual clarity 
and organization. Whitespace within methods should separate functionality, but 
having too many sections in a method often means you should refactor into
several methods.


## Brace Style

All braces get their own line after method or operation signature:

**AVOID:**

```csharp
class MyClass {
    void DoSomething() {
        if (someTest) {
          // ...
        } else {
          // ...
        }
    }
}
```

**PREFER:**

```csharp
class MyClass
{
    void DoSomething()
    {
        if (someTest)
        {
          // ...
        }
        else
        {
          // ...
        }
    }
}
```

Conditional statements are always required to be enclosed with braces,
irrespective of the number of lines required.

**AVOID:**

```csharp
if (someTest)
    doSomething();  

if (someTest) doSomethingElse();
```

**PREFER:**

```csharp
if (someTest) 
{
    DoSomething();
}  

if (someTest)
{
    DoSomethingElse();
}
```
## Switch Statements

Always handle the default case of a switch statement

**PREFER:**  
  
```csharp
switch (variable) 
{
    case 1:
        break;
    case 2:
        break;
    default:
        break;
}
```

**AVOID:**  
  
```csharp
switch (variable) 
{
    case 1:
        break;
    case 2:
        break;
}
```

## Language

Use US English spelling. Due to computer autocorrect and language settings
Ensure that all characters used, are within the latin ASCII count, avoid naming conventions inluding foreign characters.

**AVOID:**

```csharp
string colour = "red";
string एमएसजी = "नमस्ते दुनिया!";
```

**PREFER:**

```csharp
string color = "red";
string msg = "Hello, world";
```

The exception here is `MonoBehaviour` as that's what the class is actually called.
