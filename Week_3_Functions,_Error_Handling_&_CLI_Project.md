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
        "<a href=\"https://colab.research.google.com/github/mxzzmaih/Sales-Analysis/blob/master/Week_3_Functions%2C_Error_Handling_%26_CLI_Project.md\" target=\"_parent\"><img src=\"https://colab.research.google.com/assets/colab-badge.svg\" alt=\"Open In Colab\"/></a>"
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "# Week 3 Lab Solutions – Functions, Error Handling & CLI Project  \n",
        "COMP11124 – Object-Oriented Programming\n",
        "\n",
        "This week's lab introduced practical Python exercises focused on function creation, common error handling, and building an interactive CLI-based To-Do List application. Students were guided through a progression of tasks involving conditionals, loops, and debugging, culminating in a real-world mini project.\n"
      ],
      "metadata": {
        "id": "XYYG5d_A_6Mu"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "---\n",
        "\n",
        "## Exercise 1: greet_friends Function\n",
        "\n",
        "📘 **Objective:**  \n",
        "To create a function that greets each friend from a list using a loop.\n",
        "\n",
        "---\n",
        "\n",
        "### ✅ Code"
      ],
      "metadata": {
        "id": "_DNZXbih97hH"
      }
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "Cnj_OA1p96Ne",
        "outputId": "bf7810ed-fca8-465f-8e2b-5d5cc30995b7"
      },
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Hello John!\n",
            "Hello Jane!\n",
            "Hello Jack!\n"
          ]
        }
      ],
      "source": [
        "# Function to greet each friend from a list\n",
        "def greet_friends(friend_list):\n",
        "    for name in friend_list:\n",
        "        print(f\"Hello {name}!\")  # Print a greeting for each name\n",
        "\n",
        "# Example list of friends\n",
        "friend_list = [\"John\", \"Jane\", \"Jack\"]\n",
        "\n",
        "# Calling the function\n",
        "greet_friends(friend_list)\n"
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "Learning Outcome\n",
        "\n",
        "Practiced defining a Python function\n",
        "\n",
        "Used for loop to iterate over lists\n",
        "\n",
        "Reinforced function calling and parameter passing"
      ],
      "metadata": {
        "id": "Oo77ZN2E-DgZ"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "---\n",
        "\n",
        "## Exercise 2: calculate_tax Function\n",
        "\n",
        "📘 **Objective:**  \n",
        "To compute the tax amount using the provided income and tax rate.\n",
        "\n",
        "---\n",
        "\n",
        "### ✅ Code\n"
      ],
      "metadata": {
        "id": "tsozc7wI-Eru"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "\n",
        "# Function to calculate tax based on income and tax rate\n",
        "def calculate_tax(income, tax_rate):\n",
        "    return income * tax_rate  # Returns the calculated tax\n",
        "\n",
        "# Example usage\n",
        "print(\"Calculated Tax:\", calculate_tax(50000, 0.2))"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "1OE_w3v6-QDm",
        "outputId": "c8077f09-ffb3-460e-f715-5f05f534cc32"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Calculated Tax: 10000.0\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "Learning Outcome\n",
        "\n",
        "Practiced defining and calling functions with return values\n",
        "\n",
        "Applied mathematical operations in function logic\n",
        "\n",
        "Reinforced understanding of parameters and output formatting"
      ],
      "metadata": {
        "id": "5BFT4dWt-Rrr"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "---\n",
        "\n",
        "## Exercise 3: compound_interest Function\n",
        "\n",
        "📘 **Objective:**  \n",
        "To compute compound interest annually and return the final amount using a loop and mathematical formula.\n",
        "\n",
        "---\n",
        "\n",
        "### ✅ Code"
      ],
      "metadata": {
        "id": "sXRmH-Gt-VzB"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "\n",
        "# Function to calculate compound interest yearly\n",
        "def compound_interest(principal, duration, interest_rate):\n",
        "    # Validate interest rate\n",
        "    if interest_rate < 0 or interest_rate > 1:\n",
        "        print(\"Please enter a decimal number between 0 and 1\")\n",
        "        return None\n",
        "\n",
        "    # Validate duration\n",
        "    if duration < 0:\n",
        "        print(\"Please enter a positive number of years\")\n",
        "        return None\n",
        "\n",
        "    # Calculate and print total for each year\n",
        "    for year in range(1, duration + 1):\n",
        "        total = principal * (1 + interest_rate) ** year\n",
        "        print(f\"The total amount of money earned by the investment in year {year} is {round(total)} £\")\n",
        "\n",
        "    # Return final value as integer\n",
        "    return int(principal * (1 + interest_rate) ** duration)\n",
        "\n",
        "# Test with assertion\n",
        "assert compound_interest(1000, 5, 0.03) == 1159\n"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "2vQxAX0M-nZm",
        "outputId": "2b6700ad-207d-40da-d5b5-5841c2160d88"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "The total amount of money earned by the investment in year 1 is 1030 £\n",
            "The total amount of money earned by the investment in year 2 is 1061 £\n",
            "The total amount of money earned by the investment in year 3 is 1093 £\n",
            "The total amount of money earned by the investment in year 4 is 1126 £\n",
            "The total amount of money earned by the investment in year 5 is 1159 £\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "Learning Outcome\n",
        "\n",
        "Applied the concept of compound interest using loops and power operator\n",
        "\n",
        "Practiced input validation and year-wise tracking\n",
        "\n",
        "Strengthened use of assertions for testing return values"
      ],
      "metadata": {
        "id": "HWWL0yJC-o94"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "---\n",
        "\n",
        "## Exercise 4: Common Python Errors (Fixed)\n",
        "\n",
        "📘 **Objective:**  \n",
        "To identify and fix typical Python errors such as `SyntaxError`, `NameError`, `ValueError`, and `IndexError`.\n",
        "\n",
        "---\n",
        "\n",
        "### 🔹 1. SyntaxError – Missing Quote\n"
      ],
      "metadata": {
        "id": "kO0U5_Fy-s-1"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "\n",
        "# Fix: Added closing quote\n",
        "print(\"Hello, World!\")"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "Gsm_xsPE-6cQ",
        "outputId": "f5dec908-9619-43a5-d73a-d6e223dea695"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Hello, World!\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "🔹 2. NameError – Undefined Variable"
      ],
      "metadata": {
        "id": "eu8pVy3f-8pP"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# Fix: Defined the missing variable\n",
        "favorite_color = \"Blue\"\n",
        "print(\"My favorite color is\", favorite_color)\n"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "Jg-IfD2i_DCa",
        "outputId": "2f353d99-8427-4cff-f295-31b8b9088d09"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "My favorite color is Blue\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "🔹 3. ValueError – Invalid Type Conversion"
      ],
      "metadata": {
        "id": "rEQwvtDg_FDj"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "number1 = \"5\"\n",
        "number2 = 3\n",
        "result = int(number1) + number2\n",
        "print(\"The sum is:\", result)\n"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "0ghILBgi_GoO",
        "outputId": "d5111d22-bc10-4c8f-c002-4f8363387299"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "The sum is: 8\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "🔹 4. IndexError – Out-of-Range Access"
      ],
      "metadata": {
        "id": "_XF_pW65_IQw"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "fruits = [\"apple\", \"banana\", \"cherry\"]\n",
        "print(fruits[1])  # prints \"banana\"\n"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "xqX_TizQ_J3p",
        "outputId": "87c86df9-2b0e-4ccf-a436-54814ae6a409"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "banana\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "Learning Outcome\n",
        "\n",
        "Identified and corrected common beginner Python errors\n",
        "\n",
        "Understood how to handle type conversion and variable initialization\n",
        "\n",
        "Reinforced careful indexing and syntax in list and string operations\n",
        "\n",
        "\n"
      ],
      "metadata": {
        "id": "dUluvsiE_Lnc"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "---\n",
        "\n",
        "## Exercise 5: IndentationError\n",
        "\n",
        "📘 **Objective:**  \n",
        "To understand and fix indentation errors caused by improper code block alignment.\n",
        "\n",
        "---\n",
        "\n",
        "### ✅ Code\n"
      ],
      "metadata": {
        "id": "ihOjSJRQ_RKP"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "\n",
        "time = 11\n",
        "if time < 12:\n",
        "    print(\"Good morning!\")"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "Wvv6aNyF_TVm",
        "outputId": "71f9d165-2a82-4bfb-e6a9-6ce865a54777"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Good morning!\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "Learning Outcome\n",
        "\n",
        "Learned how indentation is used to define code structure in Python\n",
        "\n",
        "Identified the difference between syntax and indentation issues\n",
        "\n",
        "Improved awareness of clean formatting for functional scripts"
      ],
      "metadata": {
        "id": "YnCtqdoc_WXT"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "---\n",
        "\n",
        "## 💼 Mini Project: To-Do List Manager Application\n",
        "\n",
        "📘 **Objective:**  \n",
        "To build a basic menu-driven CLI To-Do List App that lets users add, view, and remove tasks using lists and functions.\n",
        "\n",
        "---\n",
        "\n",
        "### ✅ Code\n"
      ],
      "metadata": {
        "id": "daqpZDQX_Xs-"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "\n",
        "# Initialize empty task list\n",
        "tasks = []\n",
        "\n",
        "# Function to add a new task\n",
        "def add_task():\n",
        "    task = input(\"Enter the task: \")  # Take user input\n",
        "    tasks.append(task)  # Add task to the list\n",
        "    print(\"Task added.\")\n",
        "\n",
        "# Function to view current tasks\n",
        "def view_tasks():\n",
        "    if not tasks:\n",
        "        print(\"No tasks to show.\")\n",
        "    else:\n",
        "        for index, task in enumerate(tasks):\n",
        "            print(f\"{index + 1}. {task}\")  # Display tasks with numbers\n",
        "\n",
        "# Function to remove a task by index\n",
        "def remove_task():\n",
        "    view_tasks()\n",
        "    try:\n",
        "        index = int(input(\"Enter task number to remove: \")) - 1\n",
        "        if 0 <= index < len(tasks):\n",
        "            removed = tasks.pop(index)\n",
        "            print(f\"Task '{removed}' removed.\")\n",
        "        else:\n",
        "            print(\"Invalid task number.\")\n",
        "    except ValueError:\n",
        "        print(\"Please enter a valid number.\")\n",
        "\n",
        "# Menu loop\n",
        "while True:\n",
        "    print(\"\\n=== To-Do List Menu ===\")\n",
        "    print(\"1. Add Task\")\n",
        "    print(\"2. View Tasks\")\n",
        "    print(\"3. Remove Task\")\n",
        "    print(\"4. Exit\")\n",
        "\n",
        "    choice = input(\"Choose an option: \")\n",
        "\n",
        "    if choice == \"1\":\n",
        "        add_task()\n",
        "    elif choice == \"2\":\n",
        "        view_tasks()\n",
        "    elif choice == \"3\":\n",
        "        remove_task()\n",
        "    elif choice == \"4\":\n",
        "        print(\"Goodbye!\")\n",
        "        break\n",
        "    else:\n",
        "        print(\"Invalid choice. Try again.\")"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "SONB1e6t_i4D",
        "outputId": "f9477c0d-0a16-4fcd-da13-abe46d4d3ec2"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "\n",
            "=== To-Do List Menu ===\n",
            "1. Add Task\n",
            "2. View Tasks\n",
            "3. Remove Task\n",
            "4. Exit\n",
            "Choose an option: 1\n",
            "Enter the task: WEEK 3 LAB WORK\n",
            "Task added.\n",
            "\n",
            "=== To-Do List Menu ===\n",
            "1. Add Task\n",
            "2. View Tasks\n",
            "3. Remove Task\n",
            "4. Exit\n",
            "Choose an option: 2\n",
            "1. WEEK 3 LAB WORK\n",
            "\n",
            "=== To-Do List Menu ===\n",
            "1. Add Task\n",
            "2. View Tasks\n",
            "3. Remove Task\n",
            "4. Exit\n",
            "Choose an option: 3\n",
            "1. WEEK 3 LAB WORK\n",
            "Enter task number to remove: 1\n",
            "Task 'WEEK 3 LAB WORK' removed.\n",
            "\n",
            "=== To-Do List Menu ===\n",
            "1. Add Task\n",
            "2. View Tasks\n",
            "3. Remove Task\n",
            "4. Exit\n",
            "Choose an option: 2\n",
            "No tasks to show.\n",
            "\n",
            "=== To-Do List Menu ===\n",
            "1. Add Task\n",
            "2. View Tasks\n",
            "3. Remove Task\n",
            "4. Exit\n",
            "Choose an option: 4\n",
            "Goodbye!\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "Learning Outcome\n",
        "\n",
        "Implemented a menu-driven interface using loops and conditionals\n",
        "\n",
        "Used functions for modularity and code reuse\n",
        "\n",
        "Practiced list operations, user input, and error handling\n",
        "\n",
        "Developed a mini project demonstrating Python control flow in a real-world task"
      ],
      "metadata": {
        "id": "IhvEaSgQ_sm7"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "---\n",
        "\n",
        "## 📋 Week 3 – Final Summary\n",
        "\n",
        "This week’s lab built essential Python programming skills through a sequence of structured exercises and a mini project. The focus was on:\n",
        "\n",
        "- Writing reusable functions\n",
        "- Handling various types of errors\n",
        "- Building a real-world application using conditionals, loops, and lists\n",
        "\n",
        "---\n",
        "\n",
        "### 🔑 Key Skills Gained\n",
        "\n",
        "| Concept               | Description                                                                 |\n",
        "|-----------------------|-----------------------------------------------------------------------------|\n",
        "| Functions             | Defined, called, and reused functions with parameters and return values     |\n",
        "| Errors in Python      | Identified and fixed common errors: SyntaxError, NameError, IndexError, etc.|\n",
        "| Loops & Conditionals  | Applied `for`, `while`, `if-else`, and logical operators                    |\n",
        "| CLI Application       | Developed a text-based To-Do List Manager using modular programming         |\n",
        "| Input Validation      | Used `try...except` for error-proof user interaction                        |\n",
        "\n",
        "---\n",
        "\n",
        "### Learning Outcomes\n",
        "\n",
        "- Developed confidence in using Python to solve practical problems  \n",
        "- Strengthened foundational understanding of function definitions and control flow  \n",
        "- Experienced real-world debugging through common Python errors  \n",
        "- Created a working project using everything learned in a structured, modular approach\n",
        "\n"
      ],
      "metadata": {
        "id": "S--iXmqx_0lY"
      }
    }
  ]
}