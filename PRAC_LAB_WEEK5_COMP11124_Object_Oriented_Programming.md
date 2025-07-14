{
  "nbformat": 4,
  "nbformat_minor": 0,
  "metadata": {
    "colab": {
      "provenance": [],
      "include_colab_link": true
    },
    "kernelspec": {
      "name": "python3",
      "display_name": "Python 3"
    },
    "language_info": {
      "name": "python"
    }
  },
  "cells": [
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "view-in-github",
        "colab_type": "text"
      },
      "source": [
        "<a href=\"https://colab.research.google.com/github/mxzzmaih/Sales-Analysis/blob/master/PRAC_LAB_WEEK5_COMP11124_Object_Oriented_Programming.md\" target=\"_parent\"><img src=\"https://colab.research.google.com/assets/colab-badge.svg\" alt=\"Open In Colab\"/></a>"
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "# Week 5 Lab Solutions – Inheritance, Method Overriding & Polymorphism  \n",
        "COMP11124 – Object-Oriented Programming\n",
        "\n",
        "This week's lab focused on deepening our understanding of **inheritance**, **method overriding**, and **polymorphism** in Python. Through a series of structured tasks and examples, we explored how classes can be extended, how behavior can be modified in child classes, and how polymorphic techniques allow the same interface to behave dif\n"
      ],
      "metadata": {
        "id": "km2Pl-nyd93G"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "---\n",
        "\n",
        "## 1. Task 1: Vehicle Class (Base Class)\n",
        "\n",
        "📘 **Objective:**  \n",
        "To define a general-purpose base class `Vehicle` using object-oriented principles, which can be extended by specialized vehicle types.\n",
        "\n",
        "---\n",
        "\n",
        "### 📌 Description\n",
        "\n",
        "In this task, we created a base class `Vehicle` to represent common attributes and behavior shared by all vehicles. The class includes a constructor to initialize details like colour, weight, and max speed, along with optional attributes like range and seats.\n",
        "\n",
        "The class also includes a method `move()` that simulates motion, which can be inherited or overridden by derived classes.\n",
        "\n",
        "---\n",
        "\n",
        "### ✅ Code\n"
      ],
      "metadata": {
        "id": "dbKRg2CfexQg"
      }
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "tI7-nPIQcnRs"
      },
      "outputs": [],
      "source": [
        "# Define the base class 'Vehicle'\n",
        "class Vehicle:\n",
        "    def __init__(self, colour, weight, max_speed, max_range=None, seats=None):\n",
        "        self.colour = colour              # Colour of the vehicle\n",
        "        self.weight = weight              # Weight in kilograms\n",
        "        self.max_speed = max_speed        # Maximum speed in km/h\n",
        "        self.max_range = max_range        # Optional: range in km\n",
        "        self.seats = seats                # Optional: seating capacity\n",
        "\n",
        "    # Method to simulate movement\n",
        "    def move(self, speed):\n",
        "        print(f\"The vehicle is moving at {speed} km/h\")\n"
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "Learning Outcome\n",
        "\n",
        "Learned to define a base class with shared attributes\n",
        "\n",
        "Practiced using constructors with optional parameters\n",
        "\n",
        "Understood the concept of reusable methods for future inheritance\n",
        "\n"
      ],
      "metadata": {
        "id": "8bh9PxJWfHgz"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "---\n",
        "\n",
        "## 2. Task 2: Car Class (Inherits from Vehicle)\n",
        "\n",
        "📘 **Objective:**  \n",
        "To implement inheritance by creating a `Car` class that extends the `Vehicle` base class and overrides its behavior.\n",
        "\n",
        "---\n",
        "\n",
        "### 📌 Description\n",
        "\n",
        "This task builds on the previously defined `Vehicle` class by introducing a `Car` class. It inherits the core attributes and methods of `Vehicle` while adding a new attribute `form_factor` to describe the car's body type (e.g., SUV, Sedan).\n",
        "\n",
        "Additionally, the `move()` method is overridden to provide a more specific behavior appropriate to a car.\n",
        "\n",
        "---\n",
        "\n",
        "### ✅ Code\n"
      ],
      "metadata": {
        "id": "xq1BYgEKfWR6"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# Define the 'Car' class that inherits from Vehicle\n",
        "class Car(Vehicle):\n",
        "    def __init__(self, colour, weight, max_speed, form_factor, **kwargs):\n",
        "        # Call the constructor of Vehicle using super()\n",
        "        super().__init__(colour, weight, max_speed, **kwargs)\n",
        "        self.form_factor = form_factor  # e.g., SUV, Sedan, Hatchback\n",
        "\n",
        "    # Override the move method\n",
        "    def move(self, speed):\n",
        "        print(f\"The car is driving at {speed} km/h\")\n"
      ],
      "metadata": {
        "id": "ucXLsxlSfbDd"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "source": [
        "Learning Outcome\n",
        "\n",
        "Practiced implementing single inheritance\n",
        "\n",
        "Learned how to override methods in a child class\n",
        "\n",
        "Understood how to extend base class functionality while preserving reusability"
      ],
      "metadata": {
        "id": "WSWpYNK5fefS"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "---\n",
        "\n",
        "## 3. Task 3: Electric Car Class (Inherits from Car)\n",
        "\n",
        "📘 **Objective:**  \n",
        "To extend the `Car` class by introducing an `Electric` subclass that represents electric vehicles and overrides inherited behavior.\n",
        "\n",
        "---\n",
        "\n",
        "### 📌 Description\n",
        "\n",
        "In this task, the `Electric` class is created as a subclass of `Car`, demonstrating **multi-level inheritance**. It introduces a new attribute `battery_capacity` (measured in kWh) and overrides the `move()` method to provide additional behavior, such as displaying the maximum driving range.\n",
        "\n",
        "This example highlights how specialized behavior can be introduced in deeper inheritance hierarchies.\n",
        "\n",
        "---\n",
        "\n",
        "### ✅ Code\n",
        "\n"
      ],
      "metadata": {
        "id": "1XLHAI6zfgpE"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# Define 'Electric' class that inherits from Car\n",
        "class Electric(Car):\n",
        "    def __init__(self, colour, weight, max_speed, form_factor, battery_capacity, **kwargs):\n",
        "        super().__init__(colour, weight, max_speed, form_factor, **kwargs)\n",
        "        self.battery_capacity = battery_capacity  # Battery capacity in kWh\n",
        "\n",
        "    # Override the move method\n",
        "    def move(self, speed):\n",
        "        print(f\"The electric car is driving at {speed} km/h and has a max range of {self.max_range} km\")\n"
      ],
      "metadata": {
        "id": "GK_W7S3ffxXt"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "source": [
        "Learning Outcome\n",
        "\n",
        "Practiced multi-level inheritance in Python\n",
        "\n",
        "Understood how to override inherited methods with more specific behavior\n",
        "\n",
        "Learned how to enhance base functionality by adding new attributes in child classes\n",
        "\n"
      ],
      "metadata": {
        "id": "wmqKF2RefzRi"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "---\n",
        "\n",
        "## 4. Task 4: Petrol Car Class (Inherits from Car)\n",
        "\n",
        "📘 **Objective:**  \n",
        "To implement a subclass `Petrol` that inherits from `Car` and introduces fuel-specific properties while overriding inherited behavior.\n",
        "\n",
        "---\n",
        "\n",
        "### 📌 Description\n",
        "\n",
        "This task defines a `Petrol` class to represent petrol-based vehicles. It extends the `Car` class and includes an additional attribute `fuel_capacity`, measured in liters. The `move()` method is overridden to reflect characteristics specific to petrol vehicles, such as range.\n",
        "\n",
        "This task further demonstrates the flexibility of inheritance and method specialization in subclass design.\n",
        "\n",
        "---\n",
        "\n",
        "### ✅ Code\n"
      ],
      "metadata": {
        "id": "MLFTdlNAf1Gb"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# Define 'Petrol' class that inherits from Car\n",
        "class Petrol(Car):\n",
        "    def __init__(self, colour, weight, max_speed, form_factor, fuel_capacity, **kwargs):\n",
        "        super().__init__(colour, weight, max_speed, form_factor, **kwargs)\n",
        "        self.fuel_capacity = fuel_capacity  # Fuel capacity in litres\n",
        "\n",
        "    # Override the move method\n",
        "    def move(self, speed):\n",
        "        print(f\"The petrol car is driving at {speed} km/h and has a max range of {self.max_range} km\")\n"
      ],
      "metadata": {
        "id": "Q0pYFz4ygcj7"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "source": [
        "Learning Outcome\n",
        "\n",
        "Practiced subclassing with fuel-specific attributes\n",
        "\n",
        "Reinforced the concept of method overriding in inheritance chains\n",
        "\n",
        "Learned how to build modular and extendable class hierarchies"
      ],
      "metadata": {
        "id": "pbHyqY0egff8"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "---\n",
        "\n",
        "## 5. Task 5: Plane Class (Inherits from Vehicle)\n",
        "\n",
        "📘 **Objective:**  \n",
        "To create a subclass `Plane` that inherits from the `Vehicle` class and customizes its behavior for air-based transport.\n",
        "\n",
        "---\n",
        "\n",
        "### 📌 Description\n",
        "\n",
        "This task introduces the `Plane` class, which extends the `Vehicle` base class. It adds a new attribute `wingspan` (in meters) specific to aircraft. The inherited `move()` method is overridden to reflect the context of a flying vehicle.\n",
        "\n",
        "This example emphasizes how inheritance can be used across different categories of transport beyond just road vehicles.\n",
        "\n",
        "---\n",
        "\n",
        "### ✅ Code\n"
      ],
      "metadata": {
        "id": "d768fbsxgqJX"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# Define 'Plane' class that inherits from Vehicle\n",
        "class Plane(Vehicle):\n",
        "    def __init__(self, colour, weight, max_speed, wingspan, **kwargs):\n",
        "        super().__init__(colour, weight, max_speed, **kwargs)\n",
        "        self.wingspan = wingspan  # Wingspan in meters\n",
        "\n",
        "    # Override the move method\n",
        "    def move(self, speed):\n",
        "        print(f\"The plane is flying at {speed} km/h\")\n"
      ],
      "metadata": {
        "id": "YT-bxxncguhY"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "source": [
        "Learning Outcome\n",
        "\n",
        "Applied inheritance in a cross-domain (air travel) scenario\n",
        "\n",
        "Understood the importance of context-specific method overriding\n",
        "\n",
        "Practiced creating flexible base classes for real-world modeling"
      ],
      "metadata": {
        "id": "SFIsZsyBgw1G"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "---\n",
        "\n",
        "## 6. Task 6: Propeller Plane Class (Inherits from Plane)\n",
        "\n",
        "📘 **Objective:**  \n",
        "To extend the `Plane` class by introducing a `Propeller` subclass that adds specific attributes and custom behavior for propeller-based aircraft.\n",
        "\n",
        "---\n",
        "\n",
        "### 📌 Description\n",
        "\n",
        "This task creates a `Propeller` class, which is a more specific version of a `Plane`. It introduces the attribute `propeller_diameter` to describe the size of the propeller blades (in meters). The `move()` method is overridden to reflect that the movement is powered by a propeller engine.\n",
        "\n",
        "This highlights **multi-level inheritance** in an aviation context.\n",
        "\n",
        "---\n",
        "\n",
        "### ✅ Code"
      ],
      "metadata": {
        "id": "iHmlbqtFg6hK"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# Define 'Propeller' plane that inherits from Plane\n",
        "class Propeller(Plane):\n",
        "    def __init__(self, colour, weight, max_speed, wingspan, propeller_diameter, **kwargs):\n",
        "        super().__init__(colour, weight, max_speed, wingspan, **kwargs)\n",
        "        self.propeller_diameter = propeller_diameter  # Diameter in meters\n",
        "\n",
        "    # Override the move method\n",
        "    def move(self, speed):\n",
        "        print(f\"The propeller plane is flying at {speed} km/h\")\n"
      ],
      "metadata": {
        "id": "Z-DaTVfthA-w"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "source": [
        "Learning Outcome\n",
        "\n",
        "Practiced multi-level inheritance in a specialized use case\n",
        "\n",
        "Learned how to add unique subclass attributes while maintaining hierarchy\n",
        "\n",
        "Reinforced method overriding for context-specific behaviors\n"
      ],
      "metadata": {
        "id": "oczrwJqBhC8u"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "---\n",
        "\n",
        "## 7. Task 7: Jet Class (Inherits from Plane)\n",
        "\n",
        "📘 **Objective:**  \n",
        "To model a `Jet` aircraft by extending the `Plane` class with additional jet-specific attributes and behavior.\n",
        "\n",
        "---\n",
        "\n",
        "### 📌 Description\n",
        "\n",
        "The `Jet` class is a subclass of `Plane` that represents high-speed, engine-powered aircraft. It introduces a new attribute `engine_thrust`, which indicates the jet’s thrust power (in Newtons). The `move()` method is overridden to reflect high-speed flight specific to jets.\n",
        "\n",
        "This task reinforces the use of multi-level inheritance in aviation and specialization through method overriding.\n",
        "\n",
        "---\n",
        "\n",
        "### ✅ Code\n"
      ],
      "metadata": {
        "id": "qM6AcqnuhL7U"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# Define 'Jet' class that inherits from Plane\n",
        "class Jet(Plane):\n",
        "    def __init__(self, colour, weight, max_speed, wingspan, engine_thrust, **kwargs):\n",
        "        super().__init__(colour, weight, max_speed, wingspan, **kwargs)\n",
        "        self.engine_thrust = engine_thrust  # Thrust power in Newtons\n",
        "\n",
        "    # Override the move method\n",
        "    def move(self, speed):\n",
        "        print(f\"The jet plane is flying at {speed} km/h\")\n"
      ],
      "metadata": {
        "id": "ycAUqtRThQuf"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "source": [
        "Learning Outcome\n",
        "\n",
        "Practiced multi-level inheritance in aviation models\n",
        "\n",
        "Understood how to introduce and manage new attributes in child classes\n",
        "\n",
        "Strengthened method overriding for realistic object behavior"
      ],
      "metadata": {
        "id": "rfuqXWh0hR1J"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "---\n",
        "\n",
        "## 8. Task 8: FlyingCar Class (Multiple Inheritance)\n",
        "\n",
        "📘 **Objective:**  \n",
        "To demonstrate the concept of **multiple inheritance** in Python by creating a `FlyingCar` class that combines features of both `Car` and `Plane`.\n",
        "\n",
        "---\n",
        "\n",
        "### 📌 Description\n",
        "\n",
        "This task introduces the `FlyingCar` class, which inherits from both `Car` and `Plane`. It utilizes `super()` to follow Python’s **Method Resolution Order (MRO)** and ensure proper initialization of attributes from both parent classes.\n",
        "\n",
        "The `move()` method is overridden to reflect the dual-purpose nature of the flying car, capable of both driving and flying.\n",
        "\n",
        "---\n",
        "\n",
        "### ✅ Code"
      ],
      "metadata": {
        "id": "ko6u09sNhcnw"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# Multiple Inheritance: FlyingCar inherits from both Car and Plane\n",
        "class FlyingCar(Car, Plane):\n",
        "    def __init__(self, colour, weight, max_speed, form_factor, wingspan, **kwargs):\n",
        "        # Use super() to handle MRO (Method Resolution Order)\n",
        "        super().__init__(colour, weight, max_speed, form_factor=form_factor, wingspan=wingspan, **kwargs)\n",
        "\n",
        "    # Override the move method\n",
        "    def move(self, speed):\n",
        "        print(f\"The flying car is driving or flying at {speed} km/h\")\n"
      ],
      "metadata": {
        "id": "KwhbBcXPhU2K"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "source": [
        "Learning Outcome\n",
        "\n",
        "Practiced multiple inheritance with two parent classes\n",
        "\n",
        "Learned to use super() with MRO in complex hierarchies\n",
        "\n",
        "Understood how to combine features from unrelated classes in one unified class"
      ],
      "metadata": {
        "id": "gJxDs3Jrhj5y"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "---\n",
        "\n",
        "## 9. Task 9: Polymorphism Example (Animal)\n",
        "\n",
        "📘 **Objective:**  \n",
        "To demonstrate **polymorphism** in Python by using unrelated classes that implement the same method signature.\n",
        "\n",
        "---\n",
        "\n",
        "### 📌 Description\n",
        "\n",
        "This task introduces the `Animal` class, which contains a method `move(speed)` — similar to the method in `Vehicle` and its subclasses. Although `Animal` is not related by inheritance, it shares the same method name, allowing it to be used polymorphically in a common context.\n",
        "\n",
        "---\n",
        "\n",
        "### ✅ Code"
      ],
      "metadata": {
        "id": "XZhQjhV9h1yI"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# Define an unrelated class to show polymorphism\n",
        "class Animal:\n",
        "    def move(self, speed):\n",
        "        print(f\"The animal is moving at {speed} km/h\")\n"
      ],
      "metadata": {
        "id": "YdSWxXl1h3Zf"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "source": [
        "Learning Outcome\n",
        "\n",
        "Understood the concept of polymorphism using unrelated classes\n",
        "\n",
        "Learned how shared method signatures enable uniform behavior\n",
        "\n",
        "Practiced writing flexible code that works with different object types"
      ],
      "metadata": {
        "id": "E1fAD4lAh7BZ"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "---\n",
        "\n",
        "## 10. Task 10: Object Creation and Polymorphic Call\n",
        "\n",
        "📘 **Objective:**  \n",
        "To demonstrate **polymorphism** by creating instances of multiple classes (both related and unrelated) and invoking a common method (`move()`).\n",
        "\n",
        "---\n",
        "\n",
        "### 📌 Description\n",
        "\n",
        "This task showcases how polymorphism works by creating objects from various classes that all implement a `move()` method. Despite being from different hierarchies (or unrelated entirely like `Animal`), each object responds appropriately when `move(speed)` is called — demonstrating **runtime polymorphism** in Python.\n",
        "\n",
        "---\n",
        "\n",
        "### ✅ Code"
      ],
      "metadata": {
        "id": "RHM70aqKiEZT"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# Create instances of each class\n",
        "vehicle = Vehicle(\"Black\", 1000, 180, max_range=400)\n",
        "car = Car(\"Blue\", 1200, 220, \"SUV\", max_range=450)\n",
        "electric_car = Electric(\"White\", 1100, 200, \"Hatchback\", 80, max_range=500, seats=4)\n",
        "petrol_car = Petrol(\"Red\", 1400, 240, \"Sedan\", 50, max_range=600)\n",
        "propeller = Propeller(\"Grey\", 1300, 300, 25, 2.5, max_range=700)\n",
        "jet = Jet(\"Silver\", 2000, 900, 35, 20000, max_range=1200)\n",
        "flying_car = FlyingCar(\"Yellow\", 1300, 250, \"Hybrid\", 20, max_range=650, seats=2)\n",
        "animal = Animal()\n",
        "\n",
        "# Loop through all objects and call move()\n",
        "for obj in [vehicle, car, electric_car, petrol_car, propeller, jet, flying_car, animal]:\n",
        "    obj.move(100)\n"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "FZfrHSTdiGvi",
        "outputId": "2a6babea-5e61-4d48-de92-6966b5f28b78"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "The vehicle is moving at 100 km/h\n",
            "The car is driving at 100 km/h\n",
            "The electric car is driving at 100 km/h and has a max range of 500 km\n",
            "The petrol car is driving at 100 km/h and has a max range of 600 km\n",
            "The propeller plane is flying at 100 km/h\n",
            "The jet plane is flying at 100 km/h\n",
            "The flying car is driving or flying at 100 km/h\n",
            "The animal is moving at 100 km/h\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "Learning Outcome\n",
        "\n",
        "Applied runtime polymorphism through shared method names\n",
        "\n",
        "Understood how unrelated classes can be used polymorphically\n",
        "\n",
        "Practiced clean and scalable object-oriented design using inheritance\n",
        "\n"
      ],
      "metadata": {
        "id": "cxJ5Zzn5iL8P"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "Portfolio Exercise 4 – User and Owner Class Integration with TaskList\n"
      ],
      "metadata": {
        "id": "krvwXCGtlir5"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "Define User and Owner Classes"
      ],
      "metadata": {
        "id": "KLeVC21QlrFO"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# users.py module (in same cell for simplicity)\n",
        "\n",
        "class User:\n",
        "    def __init__(self, name, email):\n",
        "        self.name = name\n",
        "        self.email = email\n",
        "\n",
        "    def __str__(self):\n",
        "        return f\"User: {self.name} ({self.email})\"\n",
        "\n",
        "class Owner(User):\n",
        "    def __init__(self, name, email):\n",
        "        super().__init__(name, email)\n",
        "\n",
        "    def __str__(self):\n",
        "        return f\"Owner: {self.name} ({self.email})\"\n"
      ],
      "metadata": {
        "id": "5KrdYZF0lhCf"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "source": [
        "---\n",
        "\n",
        "## Portfolio Exercise 4 – User and Owner Class Integration with TaskList\n",
        "\n",
        "📘 **Objective:**  \n",
        "To define and integrate `User` and `Owner` classes, forming a base for task ownership in the modular ToDo application.\n",
        "\n",
        "---\n",
        "\n",
        "### 📌 Description\n",
        "\n",
        "This task introduces the `User` class to store basic information such as name and email, and an `Owner` class that inherits from `User`. These classes form the foundation for task ownership and can later be connected with task lists or permission layers in the application.\n",
        "\n",
        "The `__str__()` methods provide human-readable representations, which aid in logging, debugging, and UI display.\n",
        "\n",
        "---\n",
        "\n",
        "### ✅ Code"
      ],
      "metadata": {
        "id": "zvnflEh4l_Wk"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "Define Task and RecurringTask Classes"
      ],
      "metadata": {
        "id": "7gMSOJ_9mK4C"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "from datetime import datetime, timedelta\n",
        "\n",
        "# ✅ Basic task structure\n",
        "class Task:\n",
        "    def __init__(self, title, due_date):\n",
        "        self.title = title\n",
        "        self.date_due = due_date\n",
        "        self.completed = False\n",
        "        self.date_created = datetime.now()\n",
        "\n",
        "    def __str__(self):\n",
        "        return f\"Task: {self.title} | Due: {self.date_due.date()} | Completed: {self.completed}\"\n",
        "\n",
        "# 🔁 Recurring task that extends Task\n",
        "class RecurringTask(Task):\n",
        "    def __init__(self, title, due_date, interval):\n",
        "        super().__init__(title, due_date)\n",
        "        self.interval = interval                          # How often it repeats (in days)\n",
        "        self.completed_dates = []                         # List of dates when completed\n",
        "\n",
        "    def __str__(self):\n",
        "        return f\"Recurring Task: {self.title} | Every {self.interval.days} days | Due: {self.date_due.date()}\"\n"
      ],
      "metadata": {
        "id": "rLD2-khQmOsG"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "source": [
        "Learning Outcome\n",
        "\n",
        "Practiced basic class and subclass creation\n",
        "\n",
        "Understood how inheritance can be used to extend base functionality\n",
        "\n",
        "Created user identity structures for integration with task and ownership features"
      ],
      "metadata": {
        "id": "GkDSHNCamRsH"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "---\n",
        "\n",
        "## Portfolio Exercise 4 (Continued) – TaskList and Owner Integration\n",
        "\n",
        "📘 **Objective:**  \n",
        "To define a `TaskList` class that stores an `Owner` object and supports adding and viewing tasks with filtering based on completion status using `@property`.\n",
        "\n",
        "---\n",
        "\n",
        "### 📌 Description\n",
        "\n",
        "The `TaskList` class is responsible for managing a list of tasks and associating them with a specific `Owner`. It includes:\n",
        "\n",
        "- `add_task()` method to append tasks  \n",
        "- `uncompleted_tasks` as a **read-only property** to fetch pending tasks  \n",
        "- `view_tasks()` for displaying all pending tasks with owner information\n",
        "\n",
        "This implementation showcases both **composition** and **encapsulation** in object-oriented programming.\n",
        "\n",
        "---\n",
        "\n",
        "### ✅ Code\n"
      ],
      "metadata": {
        "id": "Rdadc3Gpmgul"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "from typing import List\n",
        "\n",
        "# 📌 TaskList now stores the owner of the list\n",
        "class TaskList:\n",
        "    def __init__(self, owner):\n",
        "        self.owner = owner              # Owner must be an instance of Owner\n",
        "        self.tasks: List[Task] = []     # List of Task or RecurringTask\n",
        "\n",
        "    def add_task(self, task):\n",
        "        self.tasks.append(task)\n",
        "\n",
        "    @property\n",
        "    def uncompleted_tasks(self):\n",
        "        # ✅ Property returns all tasks not marked as completed\n",
        "        return [task for task in self.tasks if not task.completed]\n",
        "\n",
        "    def view_tasks(self):\n",
        "        print(f\"\\n🧑‍💼 Task list owned by: {self.owner}\")\n",
        "        print(\"📌 Uncompleted Tasks:\")\n",
        "        for task in self.uncompleted_tasks:\n",
        "            print(f\"➡️ {task}\")\n"
      ],
      "metadata": {
        "id": "NPfflbT4mhZN"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "source": [
        "Learning Outcome\n",
        "\n",
        "Learned to bind data (tasks) with a role (owner) using object references\n",
        "\n",
        "Implemented @property to create computed, read-only attributes\n",
        "\n",
        "Applied principles of composition and encapsulation in a real-world model"
      ],
      "metadata": {
        "id": "i6ZNLbAqmjSM"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "---\n",
        "\n",
        "## Portfolio Exercise 4 – Create an Owner and Use TaskList\n",
        "\n",
        "📘 **Objective:**  \n",
        "To demonstrate the use of the `Owner` and `TaskList` classes by creating a user, adding tasks, and displaying them using the `view_tasks()` method.\n",
        "\n",
        "---\n",
        "\n",
        "### 📌 Description\n",
        "\n",
        "In this exercise, an `Owner` object is created and associated with a `TaskList`. Both standard `Task` and `RecurringTask` instances are added to the list. The method `view_tasks()` prints pending tasks assigned to that owner.\n",
        "\n",
        "This illustrates the integration of user roles with task management and dynamic task handling through composition.\n",
        "\n",
        "---\n",
        "\n",
        "### ✅ Code"
      ],
      "metadata": {
        "id": "GtzTOCtPm4WD"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# ✅ Create an owner\n",
        "owner = Owner(\"XYZ\", \"XYZ@example.com\")\n",
        "\n",
        "# ✅ Assign this owner to the task list\n",
        "task_list = TaskList(owner)\n",
        "\n",
        "# 📝 Add some example tasks\n",
        "task_list.add_task(Task(\"Prepare lecture\", datetime.now() + timedelta(days=1)))\n",
        "task_list.add_task(Task(\"Submit grades\", datetime.now() + timedelta(days=3)))\n",
        "task_list.add_task(RecurringTask(\"Weekly meeting\", datetime.now(), timedelta(days=7)))\n",
        "\n",
        "# 👀 Display tasks and owner info\n",
        "task_list.view_tasks()\n"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "xs2msbhzm45c",
        "outputId": "64114361-9bd8-4a59-9758-a842a7113ce1"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "\n",
            "🧑‍💼 Task list owned by: Owner: XYZ (XYZ@example.com)\n",
            "📌 Uncompleted Tasks:\n",
            "➡️ Task: Prepare lecture | Due: 2025-07-12 | Completed: False\n",
            "➡️ Task: Submit grades | Due: 2025-07-14 | Completed: False\n",
            "➡️ Recurring Task: Weekly meeting | Every 7 days | Due: 2025-07-11\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "Learning Outcome\n",
        "\n",
        "Demonstrated ownership and task binding using custom classes\n",
        "\n",
        "Practiced working with composition and dynamic task objects\n",
        "\n",
        "Showed real-world application of OOP for task management systems"
      ],
      "metadata": {
        "id": "1bE9QR45nBOT"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "---\n",
        "\n",
        "## Summary: Portfolio Exercise 4 – User, Owner, and TaskList Integration\n",
        "\n",
        "This exercise focused on building a modular structure for a task management application using object-oriented programming principles in Python.\n",
        "\n",
        "---\n",
        "\n",
        "### ✅ Key Concepts Practiced\n",
        "\n",
        "- **Class Inheritance:**  \n",
        "  `Owner` inherits from `User`, allowing role-based extensions.\n",
        "\n",
        "- **Composition:**  \n",
        "  `TaskList` holds an `Owner` object and manages a collection of `Task` or `RecurringTask` instances.\n",
        "\n",
        "- **Encapsulation with @property:**  \n",
        "  `uncompleted_tasks` provides a filtered, read-only view of pending tasks.\n",
        "\n",
        "- **Polymorphism (via Task and RecurringTask):**  \n",
        "  Tasks of different types behave uniformly in the task list context.\n",
        "\n",
        "- **Integration:**  \n",
        "  The entire workflow simulates real-world task tracking by assigning owners, creating tasks, and viewing pending items.\n",
        "\n",
        "---\n",
        "\n",
        "### 🧠 Learning Outcomes\n",
        "\n",
        "- Designed and connected multiple classes for modularity  \n",
        "- Demonstrated the use of `super()` for constructor chaining  \n",
        "- Implemented dynamic behavior using `@property` and method overriding  \n",
        "- Understood how to combine user roles and task logic in a clean architecture\n",
        "\n"
      ],
      "metadata": {
        "id": "4fWjK6kP8UAg"
      }
    }
  ]
}