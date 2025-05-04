# 🐾 Contoso Petting Zoo – School Visit Coordination App

This is a C# console application that coordinates school visits to the **Contoso Petting Zoo**, which is home to 18 different animal species. Visiting students are divided into groups, and each group is assigned a randomized selection of animals to visit. The students rotate through groups until they've seen all the animals.

---

## 📋 Project Overview

- Students from visiting schools are divided into groups (default: 6).
- Each group is assigned a randomized subset of the 18 zoo animals.
- Students rotate groups until all animals are visited.
- Group numbers vary depending on the school.

---

## 🏫 Visiting Schools & Groups

| School   | Number of Groups |
|----------|------------------|
| School A | 6 (default)      |
| School B | 3                |
| School C | 2                |

---

## 🧪 Features

- Dynamically assigns animals to groups based on the school
- Randomizes animal groupings to ensure a unique experience
- Prints school name and animal groupings to the console
- Simple and easy-to-modify console app structure

---

## 🛠️ Technologies Used

- C# (.NET 6+ Console Application)
- .NET CLI
- Visual Studio Code

---

## ⚙️ Setup Instructions

### Prerequisites

- [.NET SDK](https://dotnet.microsoft.com/download)
- [Visual Studio Code](https://code.visualstudio.com/)

### Steps

1. **Open Terminal** and run:

    ```bash
    dotnet new console -o ./CsharpProjects/TestProject
    ```

2. **Navigate** to the project folder:

    ```bash
    cd ./CsharpProjects/TestProject
    ```

3. **Open `Program.cs`** in Visual Studio Code, delete the existing code, and paste the following:

    ```csharp
    using System;
    using System.Collections.Generic;

    string[] pettingZoo = 
    {
        "alpacas", "capybaras", "chickens", "ducks", "emus", "geese", 
        "goats", "iguanas", "kangaroos", "lemurs", "llamas", "macaws", 
        "ostriches", "pigs", "ponies", "rabbits", "sheep", "tortoises",
    };

    Dictionary<string, int> schools = new()
    {
        { "School A", 6 },
        { "School B", 3 },
        { "School C", 2 }
    };

    foreach (var school in schools)
    {
        Console.WriteLine($"\n{school.Key} Animal Groups:\n");

        // Shuffle the animals
        var shuffledAnimals = pettingZoo.OrderBy(a => Guid.NewGuid()).ToArray();

        // Split into groups
        int groups = school.Value;
        int animalsPerGroup = (int)Math.Ceiling((double)shuffledAnimals.Length / groups);

        for (int i = 0; i < groups; i++)
        {
            var groupAnimals = shuffledAnimals
                .Skip(i * animalsPerGroup)
                .Take(animalsPerGroup);

            Console.WriteLine($"Group {i + 1}: {string.Join(", ", groupAnimals)}");
        }
    }
    ```

4. **Save the file**.

---

## 🚀 Run the App

In the terminal, from the project folder:

```bash
dotnet run
```

## Example Output
School A Animal Groups:

Group 1: ducks, lemurs, goats
Group 2: chickens, pigs, tortoises
...

School B Animal Groups:

Group 1: emus, rabbits, macaws, iguanas, capybaras, geese
...

School C Animal Groups:

Group 1: ponies, sheep, alpacas, macaws, ostriches, ducks, iguanas, pigs, chickens
...


---
## 📄 License

This project is intended for **educational purposes only** and is part of the Microsoft Learn training series.

You are free to:
- Use this code for personal learning.
- Modify it to experiment with your own features and logic.
- Share it for non-commercial, educational purposes with appropriate credit.

**Not for commercial use or redistribution.**

## 🙌 Acknowledgments

This project is inspired by hands-on training provided through [Microsoft Learn](https://learn.microsoft.com/), which offers interactive modules for learning C# and .NET development. Special thanks to the instructional team and community contributors who make this content accessible and effective for learners worldwide.

---

