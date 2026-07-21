STL — A C++ Standard-Library-Style Toolkit, Built From Scratch
> A modular C++ library that reimplements standard-library-style types using object-oriented design — my way of learning how the STL works by rebuilding pieces of it.
About
This project is a hand-built collection of C++ classes inspired by the Standard Template Library and standard types. Rather than use `std::string`, `std::list`, or date utilities, I implemented my own versions to understand the design decisions behind them: memory ownership, operator overloading, iterators, and clean, extensible interfaces.
Tech used
C++ with object-oriented design
Operator overloading, custom iterators, dynamic memory management
The rule-of-three (copy assignment, destructor, deep copy)
Polymorphism via `virtual` methods
Components
Class	What it does
`TMString`	A custom string type with deep-copy semantics and full operator overloading: `=`, `+`, `+=`, comparison operators (`<`, `<=`, `>`, `>=`, `==`, `!=`), and stream insertion (`<<`).
`TMList`	A linked list (830+ lines) with its own `Iterator` class, so the list can be traversed the way STL containers are — demonstrating the iterator pattern from the ground up.
`TMDate`	A date type with construction, comparison, and formatting behaviour.
`BigDecimal`	Groundwork for arbitrary-precision decimal handling.
Documentation & usage
```cpp
#include "TMString.cpp"

TMString a = "Hello, ";
TMString b = "world";
TMString c = a + b;        // operator+  -> "Hello, world"
a += b;                    // operator+=
if (a == c) { /* operator== */ }
cout << c << endl;         // overloaded operator<<
```
```cpp
#include "TMList.cpp"

// TMList maintains its own Iterator, so traversal mirrors STL containers —
// create the list, add elements, then walk it via the custom iterator.
```
Design highlights
Deep copies, not shallow — `TMString` manages its own heap buffer and frees it correctly, avoiding the classic double-free / dangling-pointer bugs.
Operators feel native — you use `TMString` and `TMList` with the same syntax you'd use for built-in types.
Custom iterator — `TMList` proves out the iterator abstraction that makes STL containers composable.
What I learned
How the STL earns its ergonomics: RAII and ownership, why the rule-of-three matters, how operator overloading creates natural syntax, and how iterators decouple traversal from the container's internal structure.
Status
Ongoing — expanding the container set and hardening memory safety.
---
Built by Mayank Aylani to understand the C++ Standard Library by rebuilding it.
