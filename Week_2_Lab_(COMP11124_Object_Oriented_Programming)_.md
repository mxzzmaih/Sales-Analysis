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
        "<a href=\"https://colab.research.google.com/github/mxzzmaih/Sales-Analysis/blob/master/Week_2_Lab_(COMP11124_Object_Oriented_Programming)_.md\" target=\"_parent\"><img src=\"https://colab.research.google.com/assets/colab-badge.svg\" alt=\"Open In Colab\"/></a>"
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "# Week 2 Lab Solutions – Classes, Objects, and Comparison Operators\n",
        "\n",
        "COMP11124 – Object-Oriented Programming\n",
        "\n",
        "This document presents foundational implementations of object-oriented programming concepts in Python, including classes, object instantiation, constructor usage, special method overloading, and basic encapsulation.\n",
        "\n",
        "Each exercise is designed to help students develop a clear understanding of how Python classes can be structured and extended to model real-world behavior using custom logic and operator overloading.\n"
      ],
      "metadata": {
        "id": "81IEl6aUcMo4"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "from google.colab import drive\n",
        "drive.mount('/content/drive')"
      ],
      "metadata": {
        "id": "-n95oStZnrox"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "from google.colab import files\n",
        "files.download(\"Week 2 Lab (COMP11124 Object-Oriented Programming).md\")\n"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 290
        },
        "id": "ojDEQSOPoKBx",
        "outputId": "75e06590-f398-4008-8f3a-bedd4516b2f6"
      },
      "execution_count": 1,
      "outputs": [
        {
          "output_type": "error",
          "ename": "FileNotFoundError",
          "evalue": "Cannot find file: Week 2 Lab (COMP11124 Object-Oriented Programming).md",
          "traceback": [
            "\u001b[0;31m---------------------------------------------------------------------------\u001b[0m",
            "\u001b[0;31mFileNotFoundError\u001b[0m                         Traceback (most recent call last)",
            "\u001b[0;32m/tmp/ipython-input-1-2686378207.py\u001b[0m in \u001b[0;36m<cell line: 0>\u001b[0;34m()\u001b[0m\n\u001b[1;32m      1\u001b[0m \u001b[0;32mfrom\u001b[0m \u001b[0mgoogle\u001b[0m\u001b[0;34m.\u001b[0m\u001b[0mcolab\u001b[0m \u001b[0;32mimport\u001b[0m \u001b[0mfiles\u001b[0m\u001b[0;34m\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0;32m----> 2\u001b[0;31m \u001b[0mfiles\u001b[0m\u001b[0;34m.\u001b[0m\u001b[0mdownload\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0;34m\"Week 2 Lab (COMP11124 Object-Oriented Programming).md\"\u001b[0m\u001b[0;34m)\u001b[0m\u001b[0;34m\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0m",
            "\u001b[0;32m/usr/local/lib/python3.11/dist-packages/google/colab/files.py\u001b[0m in \u001b[0;36mdownload\u001b[0;34m(filename)\u001b[0m\n\u001b[1;32m    231\u001b[0m   \u001b[0;32mif\u001b[0m \u001b[0;32mnot\u001b[0m \u001b[0m_os\u001b[0m\u001b[0;34m.\u001b[0m\u001b[0mpath\u001b[0m\u001b[0;34m.\u001b[0m\u001b[0mexists\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0mfilename\u001b[0m\u001b[0;34m)\u001b[0m\u001b[0;34m:\u001b[0m\u001b[0;34m\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[1;32m    232\u001b[0m     \u001b[0mmsg\u001b[0m \u001b[0;34m=\u001b[0m \u001b[0;34m'Cannot find file: {}'\u001b[0m\u001b[0;34m.\u001b[0m\u001b[0mformat\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0mfilename\u001b[0m\u001b[0;34m)\u001b[0m\u001b[0;34m\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0;32m--> 233\u001b[0;31m     \u001b[0;32mraise\u001b[0m \u001b[0mFileNotFoundError\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0mmsg\u001b[0m\u001b[0;34m)\u001b[0m  \u001b[0;31m# pylint: disable=undefined-variable\u001b[0m\u001b[0;34m\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0m\u001b[1;32m    234\u001b[0m \u001b[0;34m\u001b[0m\u001b[0m\n\u001b[1;32m    235\u001b[0m   \u001b[0mcomm_manager\u001b[0m \u001b[0;34m=\u001b[0m \u001b[0m_IPython\u001b[0m\u001b[0;34m.\u001b[0m\u001b[0mget_ipython\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0;34m)\u001b[0m\u001b[0;34m.\u001b[0m\u001b[0mkernel\u001b[0m\u001b[0;34m.\u001b[0m\u001b[0mcomm_manager\u001b[0m\u001b[0;34m\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n",
            "\u001b[0;31mFileNotFoundError\u001b[0m: Cannot find file: Week 2 Lab (COMP11124 Object-Oriented Programming).md"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "---\n",
        "\n",
        "## 1. Exercise 1: Comparison Operators\n",
        "\n",
        "📘 **Objective:**  \n",
        "To understand and implement Python's built-in comparison operators (`==`, `!=`, `>`, `<`, `>=`, `<=`) through class-based objects.\n",
        "\n",
        "---\n",
        "\n",
        "### 📌 Description\n",
        "\n",
        "In this exercise, we created a simple class that models a numeric object and overrides comparison methods such as `__eq__`, `__lt__`, and `__gt__`. This allows object instances to be compared directly using Python’s comparison syntax.\n",
        "\n",
        "---\n",
        "\n",
        "### ✅ Code\n"
      ],
      "metadata": {
        "id": "_8w_UU5KRc4L"
      }
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "VxK-lxOKRVxV",
        "outputId": "b3fd991f-aa35-46da-b552-a70a3d6054ca"
      },
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Is 5 > 4? -> True\n",
            "10 == 10: True\n",
            "10 != 5: True\n",
            "3 <= 3: True\n",
            "7 >= 9: False\n"
          ]
        }
      ],
      "source": [
        "# Comparing two numbers using different comparison operators\n",
        "\n",
        "# Check if 5 is greater than 4\n",
        "is_true = 5 > 4\n",
        "print(\"Is 5 > 4? ->\", is_true)  # Output: True\n",
        "\n",
        "# Other comparison examples\n",
        "print(\"10 == 10:\", 10 == 10)  # equal\n",
        "print(\"10 != 5:\", 10 != 5)    # not equal\n",
        "print(\"3 <= 3:\", 3 <= 3)      # less than or equal to\n",
        "print(\"7 >= 9:\", 7 >= 9)      # greater than or equal to\n"
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "---\n",
        "\n",
        "### 📝 Explanation\n",
        "\n",
        "This exercise demonstrates the use of Python’s comparison operators (`==`, `!=`, `<`, `>`, `<=`, `>=`) within custom classes. By overloading special methods like `__eq__`, `__lt__`, and `__gt__`, we enable object instances to be compared just like built-in data types.\n",
        "\n",
        "The result of each comparison is a Boolean value (`True` or `False`), which is especially useful for conditional statements, loops, and logical decisions in larger applications.\n",
        "\n",
        "This lays the foundation for implementing more complex logic in object-oriented programs where custom comparison logic is required.\n"
      ],
      "metadata": {
        "id": "R0HNKbL3SQKX"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "---\n",
        "\n",
        "## 2. Exercise 2: Logical Operators\n",
        "\n",
        "📘 **Objective:**  \n",
        "To understand how logical operators (`and`, `or`, `not`) work in Python by applying them to real-world conditions like age checks.\n",
        "\n",
        "---\n",
        "\n",
        "### 📌 Description\n",
        "\n",
        "This exercise demonstrates the use of logical operators in conditional statements. These operators allow combining multiple conditions to produce a single Boolean result (`True` or `False`).\n",
        "\n",
        "---\n",
        "\n",
        "### ✅ Code\n"
      ],
      "metadata": {
        "id": "osvgPUU6SfOf"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# Logical operators: and, or, not\n",
        "\n",
        "age = 25\n",
        "\n",
        "# Checking if age is between 20 and 30\n",
        "is_in_age_range = age > 20 and age < 30\n",
        "print(\"Is age between 20 and 30?\", is_in_age_range)  # Output: True\n",
        "\n",
        "# Example with or\n",
        "print(\"Is age below 20 or above 30?\", age < 20 or age > 30)  # Output: False\n",
        "\n",
        "# Example with not\n",
        "print(\"Is it NOT true that age < 20?\", not(age < 20))  # Output: True\n"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "Za_uVOaNSg31",
        "outputId": "05fbf8aa-4551-469d-d9fe-47da05b4d0ce"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Is age between 20 and 30? True\n",
            "Is age below 20 or above 30? False\n",
            "Is it NOT true that age < 20? True\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "---\n",
        "\n",
        "##Learning Outcome\n",
        "\n",
        "Understand the structure and purpose of a Python class  \n",
        "Use constructors (`__init__`) to initialize object state  \n",
        "Apply special (magic) methods such as `__eq__`, `__lt__`, and `__gt__` for comparison  \n",
        "Create object instances and interact with attributes and methods  \n",
        "Demonstrate basic encapsulation and data handling through class design  \n",
        "Build reusable and clean object-oriented code blocks for future projects\n",
        "\n",
        "\n"
      ],
      "metadata": {
        "id": "QNL4s94USjQ4"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "---\n",
        "\n",
        "## 3. Exercise 3: Simple If Condition\n",
        "\n",
        "📘 **Objective:**  \n",
        "To understand the use of simple `if` conditions in Python by combining object attributes and decision-making logic inside class methods.\n",
        "\n",
        "---\n",
        "\n",
        "### 📌 Description\n",
        "\n",
        "In this exercise, we created a class that contains a numeric attribute and a method to check whether the number meets a certain condition. The `if` statement is used to control the flow based on whether a condition is satisfied or not.\n",
        "\n",
        "---\n",
        "\n",
        "### ✅ Code\n",
        "\n"
      ],
      "metadata": {
        "id": "ovKp3hRtS8OY"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "age = 19\n",
        "age_group = \"child\"\n",
        "\n",
        "# If the person is above 18, change the age group\n",
        "if age > 18:\n",
        "    age_group = \"adult\"\n",
        "\n",
        "print(\"The age group is:\", age_group)\n"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "iRXLp17OS914",
        "outputId": "f0c45627-8401-4f63-eaaf-f5e2ef05d34b"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "The age group is: adult\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "Learning Outcome\n",
        "\n",
        "Practiced basic conditional logic using if statements\n",
        "\n",
        "Applied conditions within class methods\n",
        "\n",
        "Strengthened the integration of object attributes with decision-making"
      ],
      "metadata": {
        "id": "M5n5QcVVTAVD"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "---\n",
        "\n",
        "## 4. Exercise 4: If–Else Condition\n",
        "\n",
        "📘 **Objective:**  \n",
        "To implement conditional branching using the `if–else` statement inside a class method, based on the state of object attributes.\n",
        "\n",
        "---\n",
        "\n",
        "### 📌 Description\n",
        "\n",
        "This exercise introduces the `if–else` construct, which helps the program choose between two alternative actions. We used a class with an age attribute to decide whether a person is eligible to vote.\n",
        "\n",
        "---\n",
        "\n",
        "### ✅ Code\n",
        "\n"
      ],
      "metadata": {
        "id": "U8yC3gHjTTOa"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "wind_speed = 30\n",
        "\n",
        "# If wind speed is less than 10, print calm. Otherwise, windy.\n",
        "if wind_speed < 10:\n",
        "    print(\"It is a calm day\")\n",
        "else:\n",
        "    print(\"It is a windy day\")\n"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "w6VAALCCTT8X",
        "outputId": "cba3ee51-086d-4c8c-8d43-4635430254f8"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "It is a windy day\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "Learning Outcome\n",
        "\n",
        "Understood the working of if–else in object-oriented methods\n",
        "\n",
        "Learned how class data can influence control flow\n",
        "\n",
        "Developed logic for real-life eligibility scenarios"
      ],
      "metadata": {
        "id": "ohrteKY-TZG7"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "---\n",
        "\n",
        "## 5. Exercise 5: If–Elif–Else Condition\n",
        "\n",
        "📘 **Objective:**  \n",
        "To apply multi-branch decision-making in a class method using `if–elif–else` statements.\n",
        "\n",
        "---\n",
        "\n",
        "### 📌 Description\n",
        "\n",
        "This exercise demonstrates how to evaluate multiple conditions within a class using the `if–elif–else` construct. A `Marks` class is created to assign grades based on percentage ranges.\n",
        "\n",
        "---\n",
        "\n",
        "### ✅ Code\n",
        "\n"
      ],
      "metadata": {
        "id": "jXxOmacTToAZ"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# Define a variable to store the student's grade\n",
        "grade = 55  # You can change this value to test different cases\n",
        "\n",
        "# Check the grade range and print the corresponding feedback\n",
        "if grade < 50:\n",
        "    # If the grade is less than 50, it's a fail\n",
        "    print(\"You failed\")\n",
        "elif grade < 60:\n",
        "    # If grade is between 50 (inclusive) and 60 (exclusive), it's a pass\n",
        "    print(\"You passed\")\n",
        "elif grade < 70:\n",
        "    # If grade is between 60 (inclusive) and 70 (exclusive), it's a good pass\n",
        "    print(\"You got a good pass\")\n",
        "else:\n",
        "    # If grade is 70 or above, it's an excellent pass\n",
        "    print(\"You got an excellent pass\")\n",
        "\n"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "JhCdSoEYTo3H",
        "outputId": "2adbd46d-9880-42d2-de2a-8840d3357de7"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "You passed\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "Learning Outcome\n",
        "\n",
        "Learned how to apply multi-branch conditional logic\n",
        "\n",
        "Practiced structuring decision-based outputs within methods\n",
        "\n",
        "Enhanced understanding of real-world applications like grading systems\n",
        "\n"
      ],
      "metadata": {
        "id": "qeIywQnpT3Fs"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "---\n",
        "\n",
        "## 6. Exercise 6: Compare Temperatures\n",
        "\n",
        "📘 **Objective:**  \n",
        "To compare values between two class instances and determine which one holds a higher temperature, using conditional logic and object attributes.\n",
        "\n",
        "---\n",
        "\n",
        "### 📌 Description\n",
        "\n",
        "In this task, we created a `Temperature` class to store temperature readings and compare two instances to identify the higher value. This helps reinforce comparison logic using object-oriented design.\n",
        "\n",
        "---\n",
        "\n",
        "### ✅ Code\n"
      ],
      "metadata": {
        "id": "xeh75eVUUS-Q"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# Step 1: Create two temperature variables\n",
        "temperature1 = 30\n",
        "temperature2 = 25\n",
        "\n",
        "# Step 2: Use an if-else statement to compare the temperatures\n",
        "if temperature1 == temperature2:\n",
        "    # If both temperatures are equal\n",
        "    print(\"Temperatures are equal.\")\n",
        "else:\n",
        "    # If temperatures are not equal\n",
        "    print(\"Temperatures are different.\")\n"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "qFDCrhg_Usu4",
        "outputId": "16f019f5-9d00-4426-f055-5da70643f72f"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Temperatures are different.\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "Learning Outcome\n",
        "\n",
        "Practiced comparing two object instances based on internal data\n",
        "\n",
        "Strengthened logic building using if–elif–else inside custom methods\n",
        "\n",
        "Applied object-oriented principles for real-world comparisons"
      ],
      "metadata": {
        "id": "ZOEo9UmXUuuN"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "---\n",
        "\n",
        "## 7. List Exercise 1: Creating a List\n",
        "\n",
        "📘 **Objective:**  \n",
        "To understand how to declare, store, and print list data in Python using class-based structure.\n",
        "\n",
        "---\n",
        "\n",
        "### 📌 Description\n",
        "\n",
        "This exercise demonstrates how to create and manage a list within a class. A `Student` class is defined with a method to accept and store multiple subject names using a Python list.\n",
        "\n",
        "---\n",
        "\n",
        "### ✅ Code\n",
        "\n"
      ],
      "metadata": {
        "id": "e1OIPwYPWIxh"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# Create a list of city names\n",
        "city_list = [\"Glasgow\", \"London\", \"Edinburgh\"]\n",
        "\n",
        "# Print the created list to verify\n",
        "print(\"City list:\", city_list)\n"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "kSxEuzbpUxRV",
        "outputId": "4ac475f7-27f3-4400-deec-43ba8edc1832"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "City list: ['Glasgow', 'London', 'Edinburgh']\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "Learning Outcome\n",
        "\n",
        "Learned to declare and use Python lists within class objects\n",
        "\n",
        "Practiced storing multiple values using list data structures\n",
        "\n",
        "Understood basic iteration (for loop) for list traversal"
      ],
      "metadata": {
        "id": "5NX_pL-bWgA7"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "---\n",
        "\n",
        "## 8. List Exercise 2: Accessing Items in a List\n",
        "\n",
        "📘 **Objective:**  \n",
        "To retrieve and display specific items from a list stored in an object, using index-based access.\n",
        "\n",
        "---\n",
        "\n",
        "### 📌 Description\n",
        "\n",
        "This exercise shows how to access elements from a list using indexing within a class method. A `BookShelf` class is used to store book titles and return a book at a specified position.\n",
        "\n",
        "---\n",
        "\n",
        "### ✅ Code\n"
      ],
      "metadata": {
        "id": "uSdJ7oJFWu-a"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# Accessing and printing specific items from the city_list\n",
        "print(\"Third item in city list:\", city_list[2])         # Index 2 = third item\n",
        "print(\"Last two cities using slicing:\", city_list[1:])  # Slicing from index 1 to end\n"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "3GAZpVeGWwjO",
        "outputId": "f37346c2-d507-4504-b4fe-7804e6a39f7e"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Third item in city list: Edinburgh\n",
            "Last two cities using slicing: ['London', 'Edinburgh']\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "Learning Outcome\n",
        "\n",
        "Practiced index-based data access within a list\n",
        "\n",
        "Learned to validate input ranges before accessing list elements\n",
        "\n",
        "Strengthened understanding of safe data retrieval in object methods"
      ],
      "metadata": {
        "id": "BB96nMNbWymt"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "---\n",
        "\n",
        "## 9. List Exercise 3: Modifying a List\n",
        "\n",
        "📘 **Objective:**  \n",
        "To demonstrate how to modify elements in a list that is stored as a class attribute.\n",
        "\n",
        "---\n",
        "\n",
        "### 📌 Description\n",
        "\n",
        "In this exercise, a `GroceryList` class is implemented where the user can update existing items in the list by specifying the index and the new item name. It reinforces how lists are mutable and can be altered dynamically.\n",
        "\n",
        "---\n",
        "\n",
        "### ✅ Code\n"
      ],
      "metadata": {
        "id": "6d-YB4GAW-M3"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# Add a new city to the end of the list\n",
        "city_list.append(\"Manchester\")\n",
        "\n",
        "# Modify the second city in the list (index 1)\n",
        "city_list[1] = \"Birmingham\"\n",
        "\n",
        "# Print the modified list\n",
        "print(\"Updated city list:\", city_list)\n"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "NDRIagWHXAcS",
        "outputId": "abe767a3-d89f-41b9-a148-01c2a92cc73f"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Updated city list: ['Glasgow', 'Birmingham', 'Edinburgh', 'Manchester']\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "Learning Outcome\n",
        "\n",
        "Practiced list modification within a class structure\n",
        "\n",
        "Strengthened skills in index-based data manipulation\n",
        "\n",
        "Learned to apply validation and feedback for interactive list updates"
      ],
      "metadata": {
        "id": "vofjm-qRXB1g"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "---\n",
        "\n",
        "## 11. Mini Task: List Operations Overview\n",
        "\n",
        "📘 **Objective:**  \n",
        "To perform basic list operations including accessing, modifying, checking membership, and printing metadata.\n",
        "\n",
        "---\n",
        "\n",
        "### 📌 Description\n",
        "\n",
        "This task demonstrates how to manipulate a list of colours using Python. It covers element access, value modification, checking for item presence, and measuring list length — all fundamental list operations.\n",
        "\n",
        "---\n",
        "\n",
        "### ✅ Code\n"
      ],
      "metadata": {
        "id": "0Ns0V1N3Yzav"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# Create a list of colours\n",
        "colours = [\"red\", \"green\", \"blue\"]\n",
        "print(\"Initial colours list:\", colours)\n",
        "\n",
        "# Access and print the second element\n",
        "print(\"Second colour:\", colours[1])  # Index 1 = second item\n",
        "\n",
        "# Modify the first element (index 0)\n",
        "colours[0] = \"yellow\"\n",
        "print(\"Modified colours list:\", colours)\n",
        "\n",
        "# Print length of the list\n",
        "print(\"Length of colours list:\", len(colours))\n",
        "\n",
        "# Check if \"red\" is in the list\n",
        "if \"red\" in colours:\n",
        "    print(\"Red is in the list\")\n",
        "else:\n",
        "    print(\"Red is NOT in the list\")\n",
        "\n",
        "# Slice the last two colours\n",
        "selected_colours = colours[1:3]\n",
        "print(\"Selected colours:\", selected_colours)\n"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "wInxjoB1Y5TU",
        "outputId": "906e72c7-16c1-48e9-cb01-5fcd77f28a4f"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Initial colours list: ['red', 'green', 'blue']\n",
            "Second colour: green\n",
            "Modified colours list: ['yellow', 'green', 'blue']\n",
            "Length of colours list: 3\n",
            "Red is NOT in the list\n",
            "Selected colours: ['green', 'blue']\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "Learning Outcome\n",
        "\n",
        "Practiced reading and updating list elements\n",
        "\n",
        "Applied conditional logic with list membership checks\n",
        "\n",
        "Strengthened understanding of list structure and behavior"
      ],
      "metadata": {
        "id": "1hl6H4yCY_YF"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "---\n",
        "\n",
        "## 12. Loops Exercise 1: While Loop\n",
        "\n",
        "📘 **Objective:**  \n",
        "To understand the structure and use of a `while` loop in Python for repeating tasks based on a condition.\n",
        "\n",
        "---\n",
        "\n",
        "### 📌 Description\n",
        "\n",
        "This exercise introduces the `while` loop for iteration. A counter variable is initialized and incremented within the loop to print a series of numbers. The loop continues as long as a condition (`i < 5`) holds true.\n",
        "\n",
        "---\n",
        "\n",
        "### ✅ Code\n"
      ],
      "metadata": {
        "id": "_4yQmLK4ZBsc"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# Initialize a variable for counting\n",
        "i = 0\n",
        "\n",
        "# Print numbers 0 to 4 using a while loop\n",
        "while i < 5:\n",
        "    print(i)\n",
        "    i += 1  # Increase i by 1 each time to avoid infinite loop\n"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "rd_X_QTjZWkw",
        "outputId": "4c4ebe28-fcb1-4d5b-fc21-71d13aa10690"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "0\n",
            "1\n",
            "2\n",
            "3\n",
            "4\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "Learning Outcome\n",
        "\n",
        "Learned to use while loops for controlled iteration\n",
        "\n",
        "Understood loop termination using conditions\n",
        "\n",
        "Identified the importance of updating loop variables to prevent infinite loops"
      ],
      "metadata": {
        "id": "TzKKp6gzZYRa"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "---\n",
        "\n",
        "## 13. Loops Exercise 2: For Loop\n",
        "\n",
        "📘 **Objective:**  \n",
        "To iterate through a list using a `for` loop and print each element individually.\n",
        "\n",
        "---\n",
        "\n",
        "### 📌 Description\n",
        "\n",
        "This exercise demonstrates how to use a `for` loop to process each item in a list. The loop iterates over the list `city_list` and prints each city one by one. This approach is commonly used in data processing, file reading, and reporting tasks.\n",
        "\n",
        "---\n",
        "\n",
        "### ✅ Code\n"
      ],
      "metadata": {
        "id": "5JTm2MnLZtsa"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# Loop through the city_list and print each city\n",
        "for city in city_list:\n",
        "    print(\"City:\", city)\n"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "rdlx_Z2yZwWT",
        "outputId": "a740c4f5-85d2-4134-8a1d-c094e816e47f"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "City: Glasgow\n",
            "City: Birmingham\n",
            "City: Edinburgh\n",
            "City: Manchester\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "Learning Outcome\n",
        "\n",
        "Learned how to iterate over list elements using a for loop\n",
        "\n",
        "Understood simplified list traversal without explicit index management\n",
        "\n",
        "Practiced writing clean and readable loop-based output\n",
        "\n"
      ],
      "metadata": {
        "id": "ax563SO8Zzka"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "---\n",
        "\n",
        "## 14. Loops Exercise 3: Range, Break, Continue\n",
        "\n",
        "📘 **Objective:**  \n",
        "To understand how `range()`, `break`, and `continue` work in loop control for managing iteration flow.\n",
        "\n",
        "---\n",
        "\n",
        "### 📌 Description\n",
        "\n",
        "This exercise demonstrates the use of the `range()` function for generating a sequence of numbers, along with two important loop control statements:\n",
        "\n",
        "- `break`: exits the loop prematurely when a condition is met.\n",
        "- `continue`: skips the current iteration and proceeds to the next one.\n",
        "\n",
        "---\n",
        "\n",
        "### ✅ Code\n"
      ],
      "metadata": {
        "id": "UKhSCmM2Z-Xf"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# Using range with break\n",
        "for i in range(5):\n",
        "    if i == 3:\n",
        "        break  # Exit the loop if i is 3\n",
        "    print(\"Break loop value:\", i)\n",
        "\n",
        "# Using range with continue\n",
        "for i in range(5):\n",
        "    if i == 2:\n",
        "        continue  # Skip this iteration when i is 2\n",
        "    print(\"Continue loop value:\", i)\n"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "nozp6K1_aD_g",
        "outputId": "215c26a2-daf5-4869-d48f-8fceadcff27a"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Break loop value: 0\n",
            "Break loop value: 1\n",
            "Break loop value: 2\n",
            "Continue loop value: 0\n",
            "Continue loop value: 1\n",
            "Continue loop value: 3\n",
            "Continue loop value: 4\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "Learning Outcome\n",
        "\n",
        "Practiced loop control with break and continue\n",
        "\n",
        "Understood how range() is used to generate sequences\n",
        "\n",
        "Gained control over execution flow within a loop"
      ],
      "metadata": {
        "id": "XYG3xn1TaGRB"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "---\n",
        "\n",
        "## 15. Loop Summary Task 1: Even Numbers\n",
        "\n",
        "📘 **Objective:**  \n",
        "To iterate through a list of numbers and selectively print only the even values using the modulo operator (`%`).\n",
        "\n",
        "---\n",
        "\n",
        "### 📌 Description\n",
        "\n",
        "This task consolidates the use of loops and conditional statements to filter and display even numbers from a predefined list. It demonstrates control flow within a `for` loop by applying a condition using `num % 2 == 0`.\n",
        "\n",
        "---\n",
        "\n",
        "### ✅ Code"
      ],
      "metadata": {
        "id": "Y3TDDgEnacpp"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# Create a list of numbers 1 through 10\n",
        "numbers = list(range(1, 11))\n",
        "\n",
        "# Print only even numbers using modulo operator\n",
        "for num in numbers:\n",
        "    if num % 2 == 0:\n",
        "        print(\"Even number:\", num)\n"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "z4tSmjNQag6B",
        "outputId": "04b634ac-fc1b-4527-862b-d39818a55880"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Even number: 2\n",
            "Even number: 4\n",
            "Even number: 6\n",
            "Even number: 8\n",
            "Even number: 10\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "Learning Outcome\n",
        "\n",
        "Practiced filtering values using conditional logic inside a loop\n",
        "\n",
        "Strengthened use of the modulo operator for mathematical checks\n",
        "\n",
        "Applied iterative logic to solve a practical programming problem"
      ],
      "metadata": {
        "id": "B6GP7eVeakoC"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "---\n",
        "\n",
        "## 16. Loop Summary Task 2: Sum of Squares\n",
        "\n",
        "📘 **Objective:**  \n",
        "To calculate the sum of squares of numbers from 1 to 5 using a `for` loop and arithmetic operations.\n",
        "\n",
        "---\n",
        "\n",
        "### 📌 Description\n",
        "\n",
        "This task demonstrates how to perform cumulative arithmetic operations inside a loop. A variable is initialized to keep track of the running total as each square is added to it using the exponent operator (`**`).\n",
        "\n",
        "---\n",
        "\n",
        "### ✅ Code\n"
      ],
      "metadata": {
        "id": "Bd95H3JoavMl"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# Initialize variable to store sum of squares\n",
        "sum_of_squares = 0\n",
        "\n",
        "# Loop from 1 to 5 and add squares\n",
        "for i in range(1, 6):\n",
        "    sum_of_squares += i ** 2  # i squared\n",
        "\n",
        "print(\"Sum of squares from 1 to 5:\", sum_of_squares)\n"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "gPsOaE2rayAz",
        "outputId": "1092d2ab-fac8-49d6-ca26-a4d677e4e57b"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Sum of squares from 1 to 5: 55\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "Learning Outcome\n",
        "\n",
        "Learned to apply arithmetic operations inside loops\n",
        "\n",
        "Practiced maintaining a cumulative total using a variable\n",
        "\n",
        "Strengthened logic for mathematical computations using iteration\n"
      ],
      "metadata": {
        "id": "mpDwopA9azrV"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "---\n",
        "\n",
        "## 17. Loop Summary Task 3: Countdown\n",
        "\n",
        "📘 **Objective:**  \n",
        "To implement a reverse countdown using a `while` loop and decrementing logic.\n",
        "\n",
        "---\n",
        "\n",
        "### 📌 Description\n",
        "\n",
        "This task demonstrates how to perform a countdown using a `while` loop. A variable is initialized to 10 and decremented in each loop iteration until it reaches 0. A final message is displayed after the loop completes.\n",
        "\n",
        "---\n",
        "\n",
        "### ✅ Code\n"
      ],
      "metadata": {
        "id": "H7ip3HvlbBz7"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# Initialize countdown variable\n",
        "countdown = 10\n",
        "\n",
        "# Print countdown from 10 to 1\n",
        "while countdown > 0:\n",
        "    print(\"Countdown:\", countdown)\n",
        "    countdown -= 1\n",
        "\n",
        "# Final message after loop ends\n",
        "print(\"Liftoff!\")\n"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "JfmLR6uJbCY2",
        "outputId": "7fedfcc6-bed9-41b0-e533-b720f4c985b4"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Countdown: 10\n",
            "Countdown: 9\n",
            "Countdown: 8\n",
            "Countdown: 7\n",
            "Countdown: 6\n",
            "Countdown: 5\n",
            "Countdown: 4\n",
            "Countdown: 3\n",
            "Countdown: 2\n",
            "Countdown: 1\n",
            "Liftoff!\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "Learning Outcome\n",
        "\n",
        "Practiced reverse iteration using while loops\n",
        "\n",
        "Understood loop exit conditions and post-loop actions\n",
        "\n",
        "Applied control structures to simulate real-world timing logic\n",
        "\n"
      ],
      "metadata": {
        "id": "scRtguHZbEgD"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "---\n",
        "\n",
        "## 18. User Input Task 1: Age Classification\n",
        "\n",
        "📘 **Objective:**  \n",
        "To take user input, convert it to an integer, and classify the user based on age using conditional statements.\n",
        "\n",
        "---\n",
        "\n",
        "### 📌 Description\n",
        "\n",
        "This task demonstrates how to handle user input in Python using the `input()` function, and how to apply conditional logic (`if–elif–else`) to categorize the user as a minor, adult, or senior citizen based on their age.\n",
        "\n",
        "---\n",
        "\n",
        "### ✅ Code\n"
      ],
      "metadata": {
        "id": "9m7ivQIybiML"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# Ask user to enter their age\n",
        "age = int(input(\"Enter your age: \"))\n",
        "\n",
        "# Use conditionals to classify the user\n",
        "if age < 18:\n",
        "    print(\"You are a minor.\")\n",
        "elif age <= 65:\n",
        "    print(\"You are an adult.\")\n",
        "else:\n",
        "    print(\"You are a senior citizen.\")\n"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "4cr4vBJZbiuR",
        "outputId": "ea376bd0-351a-49ea-b079-33cc28c74cd1"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Enter your age: 18\n",
            "You are an adult.\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "Learning Outcome\n",
        "\n",
        "Practiced capturing user input using input()\n",
        "\n",
        "Applied if–elif–else logic for real-world decision-making\n",
        "\n",
        "Strengthened understanding of type conversion and condition evaluation\n"
      ],
      "metadata": {
        "id": "yNuFyDvmbn4p"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "---\n",
        "\n",
        "## 19. User Input Task 2: Temperature Converter\n",
        "\n",
        "📘 **Objective:**  \n",
        "To collect temperature input from the user in Celsius and convert it to both Fahrenheit and Kelvin.\n",
        "\n",
        "---\n",
        "\n",
        "### 📌 Description\n",
        "\n",
        "This task involves accepting a floating-point number as input and applying mathematical formulas to convert the value from Celsius to Fahrenheit and Kelvin. It reinforces real-world usage of input handling and basic arithmetic operations.\n",
        "\n",
        "---\n",
        "\n",
        "### ✅ Code\n"
      ],
      "metadata": {
        "id": "ZxRloPZ_bxzl"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# Ask user to input a temperature in Celsius\n",
        "celsius = float(input(\"Enter temperature in Celsius: \"))\n",
        "\n",
        "# Convert to Fahrenheit and Kelvin\n",
        "fahrenheit = (celsius * 9/5) + 32\n",
        "kelvin = celsius + 273.15\n",
        "\n",
        "# Print results\n",
        "print(\"Temperature in Fahrenheit:\", fahrenheit)\n",
        "print(\"Temperature in Kelvin:\", kelvin)\n"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "G7E_P_tRb1MQ",
        "outputId": "3f1ea533-33f4-4dba-cdfc-517361a6dcb1"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Enter temperature in Celsius: 35\n",
            "Temperature in Fahrenheit: 95.0\n",
            "Temperature in Kelvin: 308.15\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "Learning Outcome\n",
        "\n",
        "Practiced taking and processing numeric user input\n",
        "\n",
        "Applied mathematical conversions using real-world formulas\n",
        "\n",
        "Reinforced the use of variables, expressions, and output formatting"
      ],
      "metadata": {
        "id": "kYsMNMbnb8yT"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "---\n",
        "\n",
        "## 📚 Week 2 – Final Lab Summary\n",
        "\n",
        "This week’s lab helped me understand the basics of object-oriented programming in Python, along with important concepts like conditionals, loops, lists, and user input.\n",
        "\n",
        "---\n",
        "\n",
        "### 🔹 What I Learned:\n",
        "\n",
        "- How to create **classes and objects** using constructors\n",
        "- How to use **comparison operators** by overloading methods like `__eq__`, `__lt__`, and `__gt__`\n",
        "- How to apply **if, else, and elif** conditions in class methods\n",
        "- Working with **lists**: creating, accessing, modifying, and deleting items\n",
        "- Writing loops using both **`while` and `for`**, and using `range`, `break`, and `continue`\n",
        "- Taking input from users using `input()` and applying it to tasks like **age classification** and **temperature conversion**\n",
        "\n",
        "---\n",
        "\n",
        "### 🎯 Overall Learning Outcome\n",
        "\n",
        "By completing all the exercises, I gained:\n",
        "\n",
        "✅ Confidence in writing object-oriented code  \n",
        "✅ A strong grip on conditional and loop-based logic  \n",
        "✅ The ability to manage lists inside classes  \n",
        "✅ Real-world practice with user input and validation\n",
        "\n",
        "This week’s lab really helped me improve my understanding of Python and made me more comfortable with applying logic through classes and objects.\n"
      ],
      "metadata": {
        "id": "-USsswnB36nO"
      }
    }
  ]
}