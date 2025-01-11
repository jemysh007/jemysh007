PHP OOP Concepts

This document explains PHP Object-Oriented Programming (OOP) concepts with real-world examples and filenames for each implementation.


---

Table of Contents

1. Classes and Objects


2. Constructors and Destructors


3. Properties and Methods


4. Inheritance


5. Access Modifiers


6. Polymorphism


7. Abstraction


8. Interfaces


9. Static Methods and Properties


10. Traits


11. Namespaces




---

1. Classes and Objects

Filename: CarExample.php

<?php
class Car {
    public $brand;
    public $color;

    public function displayDetails() {
        return "This is a $this->color $this->brand.";
    }
}

$car = new Car();
$car->brand = "Toyota";
$car->color = "Red";
echo $car->displayDetails(); // Output: This is a Red Toyota.
?>


---

2. Constructors and Destructors

Filename: LaptopExample.php

<?php
class Laptop {
    public $brand;

    public function __construct($brand) {
        $this->brand = $brand;
        echo "Laptop created: $this->brand\n";
    }

    public function __destruct() {
        echo "Laptop destroyed: $this->brand\n";
    }
}

$laptop = new Laptop("Dell");
// Destructor is automatically called at the end of the script.
?>


---

3. Properties and Methods

Filename: PersonExample.php

<?php
class Person {
    public $name;

    public function greet() {
        return "Hello, my name is $this->name.";
    }
}

$person = new Person();
$person->name = "John";
echo $person->greet(); // Output: Hello, my name is John.
?>


---

4. Inheritance

Filename: AnimalInheritance.php

<?php
class Animal {
    public $name;

    public function makeSound() {
        return "$this->name makes a sound.";
    }
}

class Dog extends Animal {
    public function makeSound() {
        return "$this->name barks.";
    }
}

$dog = new Dog();
$dog->name = "Buddy";
echo $dog->makeSound(); // Output: Buddy barks.
?>


---

5. Access Modifiers

Filename: AccessModifiers.php

<?php
class Example {
    public $publicProperty = "Public";
    protected $protectedProperty = "Protected";
    private $privateProperty = "Private";

    public function getProperties() {
        return "$this->publicProperty, $this->protectedProperty, $this->privateProperty";
    }
}

$obj = new Example();
echo $obj->publicProperty; // Output: Public
echo $obj->getProperties(); // Output: Public, Protected, Private
?>


---

6. Polymorphism

Filename: PolymorphismExample.php

<?php
class Shape {
    public function draw() {
        return "Drawing a shape.";
    }
}

class Circle extends Shape {
    public function draw() {
        return "Drawing a circle.";
    }
}

function renderShape(Shape $shape) {
    echo $shape->draw();
}

$circle = new Circle();
renderShape($circle); // Output: Drawing a circle.
?>


---

7. Abstraction

Filename: AbstractClassExample.php

<?php
abstract class Vehicle {
    abstract public function move();
}

class Car extends Vehicle {
    public function move() {
        return "Car is moving.";
    }
}

$car = new Car();
echo $car->move(); // Output: Car is moving.
?>


---

8. Interfaces

Filename: InterfaceExample.php

<?php
interface Flyable {
    public function fly();
}

class Bird implements Flyable {
    public function fly() {
        return "Bird is flying.";
    }
}

$bird = new Bird();
echo $bird->fly(); // Output: Bird is flying.
?>


---

9. Static Methods and Properties

Filename: StaticExample.php

<?php
class MathUtils {
    public static $pi = 3.14;

    public static function add($a, $b) {
        return $a + $b;
    }
}

echo MathUtils::$pi; // Output: 3.14
echo MathUtils::add(5, 10); // Output: 15
?>


---

10. Traits

Filename: TraitExample.php

<?php
trait Logger {
    public function log($message) {
        echo "Log: $message\n";
    }
}

class Application {
    use Logger;
}

$app = new Application();
$app->log("Application started."); // Output: Log: Application started.
?>


---

11. Namespaces

Filename: NamespaceExample.php

<?php
namespace App\Models;

class User {
    public function getName() {
        return "John Doe";
    }
}

$user = new \App\Models\User();
echo $user->getName(); // Output: John Doe
?>


---

This structure provides a clear overview of PHP OOP concepts, complete with filenames for better organization.

