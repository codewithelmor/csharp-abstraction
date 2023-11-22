# csharp-abstraction-
Pillars of Object-Oriented Programming (OOP) - Abstraction

**`Abstraction`** is a concept in Object-Oriented Programming (OOP) that allows you to provide a simplified view of an entity by exposing only essential features and hiding unnecessary details. In C#, abstraction is often achieved through abstract classes and interfaces. Here's an example using an abstract class:

```csharp
using System;

// Abstract class
abstract class Shape
{
    public string Name { get; set; }

    // Constructor
    public Shape(string name)
    {
        Name = name;
    }

    // Abstract method (to be implemented by derived classes)
    public abstract double CalculateArea();

    // Concrete method
    public void DisplayInfo()
    {
        Console.WriteLine($"Shape: {Name}");
    }
}

// Concrete derived class 1
class Circle : Shape
{
    public double Radius { get; set; }

    // Constructor
    public Circle(string name, double radius) : base(name)
    {
        Radius = radius;
    }

    // Implementation of the abstract method
    public override double CalculateArea()
    {
        return Math.PI * Math.Pow(Radius, 2);
    }
}

// Concrete derived class 2
class Rectangle : Shape
{
    public double Width { get; set; }
    public double Height { get; set; }

    // Constructor
    public Rectangle(string name, double width, double height) : base(name)
    {
        Width = width;
        Height = height;
    }

    // Implementation of the abstract method
    public override double CalculateArea()
    {
        return Width * Height;
    }
}

class Program
{
    static void Main()
    {
        // Create instances of concrete classes
        Circle circle = new Circle("Circle 1", 5);
        Rectangle rectangle = new Rectangle("Rectangle 1", 4, 6);

        // Use abstraction to treat different shapes uniformly
        DisplayShapeInfo(circle);
        DisplayShapeInfo(rectangle);
    }

    static void DisplayShapeInfo(Shape shape)
    {
        shape.DisplayInfo();
        Console.WriteLine($"Area: {shape.CalculateArea()}");
        Console.WriteLine();
    }
}
```

In this example:

* The **`Shape`** class is an abstract class that defines a property **`Name`**, a constructor, a concrete method **`DisplayInfo`**, and an abstract method **`CalculateArea`**. The abstract method is meant to be implemented by derived classes.
* The **`Circle`** and **`Rectangle`** classes are concrete derived classes that inherit from the **`Shape`** class. They provide implementations for the abstract method **`CalculateArea`**.
* The **`Program`** class demonstrates how abstraction allows you to treat different shapes uniformly. The **`DisplayShapeInfo`** method takes a **`Shape`** parameter, and you can pass instances of both **`Circle`** and **`Rectangle`** to it.

Abstraction allows you to create a common interface for related classes while hiding the implementation details. This makes the code more modular, extensible, and easier to understand.
