# 🐍 Introduction to Object-Oriented Programming in Python

Embark on a journey into the heart of Python programming with our comprehensive course offering a foundation in the principles and practices of object-oriented programming (OOP). Through a series of hands-on exercises and real-world examples, learners will gain proficiency in leveraging the power of Python's OOP paradigm to create efficient, modular, and reusable code.

--------------

[OOP Fundamentals](https://github.com/janaom/datacamp-professional-data-engineer-in-python/blob/main/introduction-to-object-oriented-programming-in-python/README.md#oop-fundamentals)

Inheritance and Polymorphism

Integrating with Standard Python

-----------------

# OOP Fundamentals

Learn what object-oriented programming (OOP) is, how it differs from procedural programming, and how it can be applied. You'll define your own custom classes containing methods, attributes, and constructors, and use them to create objects!

---------------

![image](https://github.com/user-attachments/assets/523e6e8c-e3b3-4646-8d39-25883d6faa7f)


## Exercise: Exploring objects and classes

The best way to learn how to write object-oriented code is to study the design of existing classes.

In this exercise, you will explore objects of different classes to learn more about their attributes and methods.

  1) Print all possible attributes and methods for the ratio object.

  2) Repeat this for the float class.

## Solution

```python
ratio = 12 / 8

# List all attributes and methods for the ratio object
print(dir(ratio))

# Result: ['__abs__', '__add__', '__bool__', '__ceil__', '__class__', '__delattr__', '__dir__', '__divmod__', '__doc__', '__eq__', '__float__', '__floor__', '__floordiv__', '__format__', '__ge__', '__getattribute__', '__getformat__', '__getnewargs__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__int__', '__le__', '__lt__', '__mod__', '__mul__', '__ne__', '__neg__', '__new__', '__pos__', '__pow__', '__radd__', '__rdivmod__', '__reduce__', '__reduce_ex__', '__repr__', '__rfloordiv__', '__rmod__', '__rmul__', '__round__', '__rpow__', '__rsub__', '__rtruediv__', '__set_format__', '__setattr__', '__sizeof__', '__str__', '__sub__', '__subclasshook__', '__truediv__', '__trunc__', 'as_integer_ratio', 'conjugate', 'fromhex', 'hex', 'imag', 'is_integer', 'real']

# List all attributes and methods for the float class
print(dir(float))

# Result: ['__abs__', '__add__', '__bool__', '__ceil__', '__class__', '__delattr__', '__dir__', '__divmod__', '__doc__', '__eq__', '__float__', '__floor__', '__floordiv__', '__format__', '__ge__', '__getattribute__', '__getformat__', '__getnewargs__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__int__', '__le__', '__lt__', '__mod__', '__mul__', '__ne__', '__neg__', '__new__', '__pos__', '__pow__', '__radd__', '__rdivmod__', '__reduce__', '__reduce_ex__', '__repr__', '__rfloordiv__', '__rmod__', '__rmul__', '__round__', '__rpow__', '__rsub__', '__rtruediv__', '__set_format__', '__setattr__', '__sizeof__', '__str__', '__sub__', '__subclasshook__', '__truediv__', '__trunc__', 'as_integer_ratio', 'conjugate', 'fromhex', 'hex', 'imag', 'is_integer', 'real']
```

The output of dir(ratio) will be a list containing:

- Methods: Functions that can be called on the float object (e.g., __add__, __str__, as_integer_ratio, is_integer, etc.). These methods perform operations on the floating-point number.

- Attributes: Variables associated with the float object. These are typically less numerous for simple data types. You might see things like __class__ (which tells you the type of object), and __doc__ (which gives you the documentation string for the float type).
