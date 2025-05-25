# python-OOPS

Here is a ** explanation of Object-Oriented Programming (OOP) in Python**, covering all key concepts with examples and how they are used in real-world applications:

---

## 🧠 What is OOP in Python?

**Object-Oriented Programming (OOP)** is a programming paradigm that models real-world entities as **objects** with **attributes (data)** and **methods (functions)**.
Python supports OOP natively and allows you to build scalable, maintainable, and reusable code.

---

## 🔹 1. **Class and Object**

* **Class**: A blueprint for creating objects.
* **Object**: An instance of a class.

```python
class Person:
    def __init__(self, name, age):  # Constructor
        self.name = name
        self.age = age

    def greet(self):
        print(f"Hi, I'm {self.name} and I'm {self.age} years old.")

# Object creation
p1 = Person("Alice", 25)
p1.greet()
```

---

## 🔹 2. **Encapsulation**

Encapsulation means **restricting access** to internal data.
Use **private (`__`)** or **protected (`_`)** attributes to hide them from external access.

```python
class BankAccount:
    def __init__(self):
        self.__balance = 0  # private variable

    def deposit(self, amount):
        if amount > 0:
            self.__balance += amount

    def get_balance(self):
        return self.__balance

acc = BankAccount()
acc.deposit(500)
print(acc.get_balance())  # ✅ Safe access
# print(acc.__balance)  ❌ Will raise AttributeError
```

---

## 🔹 3. **Inheritance**

Allows a class to inherit attributes and methods from another class.

```python
class Animal:
    def speak(self):
        print("Animal speaks")

class Dog(Animal):  # Inheriting Animal
    def speak(self):
        print("Dog barks")

d = Dog()
d.speak()
```

---

## 🔹 4. **Polymorphism**

Same method name behaves differently in different classes.

```python
class Cat:
    def speak(self):
        print("Meow")

class Cow:
    def speak(self):
        print("Moo")

def animal_sound(animal):
    animal.speak()

animal_sound(Cat())  # Meow
animal_sound(Cow())  # Moo
```

---

## 🔹 5. **Abstraction**

Hiding implementation details using **abstract base classes**.

```python
from abc import ABC, abstractmethod

class Vehicle(ABC):
    @abstractmethod
    def start_engine(self):
        pass

class Car(Vehicle):
    def start_engine(self):
        print("Car engine started")

c = Car()
c.start_engine()
```

---

## 🔹 6. **Constructor (`__init__`)**

A special method called when an object is created.

```python
class User:
    def __init__(self, username):
        self.username = username
```

---

## 🔹 7. **Static and Class Methods**

* **Static Method**: Doesn't need class or instance.
* **Class Method**: Accesses the class (`cls`) instead of the instance (`self`).

```python
class Math:
    @staticmethod
    def add(x, y):
        return x + y

    @classmethod
    def description(cls):
        return "Performs mathematical operations"

print(Math.add(2, 3))         # 5
print(Math.description())     # Performs mathematical operations
```

---

## 🔹 8. **Magic Methods (`__str__`, `__len__`, `__add__`, etc.)**

Used to define custom behavior for built-in operations.

```python
class Book:
    def __init__(self, title):
        self.title = title

    def __str__(self):
        return f"Book: {self.title}"

book = Book("Python Basics")
print(book)  # Book: Python Basics
```

---

## 📌 Real-world Example: Library System

```python
class Book:
    def __init__(self, title, author):
        self.title = title
        self.author = author

    def info(self):
        return f"{self.title} by {self.author}"

class Library:
    def __init__(self):
        self.__books = []  # encapsulation

    def add_book(self, book):
        self.__books.append(book)

    def list_books(self):
        for book in self.__books:
            print(book.info())

lib = Library()
lib.add_book(Book("1984", "George Orwell"))
lib.add_book(Book("Sapiens", "Yuval Noah Harari"))
lib.list_books()
```

---

## 🧩 Summary

| Concept       | Keyword/Method                  | Purpose                              |
| ------------- | ------------------------------- | ------------------------------------ |
| Class/Object  | `class`, `object`               | Blueprint and instance               |
| Encapsulation | `__var`, `get_()`               | Hides internal data                  |
| Inheritance   | `class B(A)`                    | Reuse and extend                     |
| Polymorphism  | `method override`               | Different behavior, same method name |
| Abstraction   | `ABC`, `@abstractmethod`        | Hide complexity, enforce contracts   |
| Static/Class  | `@staticmethod`, `@classmethod` | Utility methods                      |

