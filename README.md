# C#
A comprehensive guide to learning C#
# Complete C# Learning Guide

A comprehensive roadmap to mastering C# from beginner to advanced level with detailed explanations and practical examples.

## Table of Contents
- [Getting Started](#getting-started)
- [Learning Path](#learning-path)
- [Development Environment](#development-environment)
- [Phase 1: Foundations](#phase-1-foundations)
- [Phase 2: Intermediate](#phase-2-intermediate)
- [Phase 3: Advanced](#phase-3-advanced)
- [Frameworks & Libraries](#frameworks--libraries)
- [Practice Projects](#practice-projects)
- [Resources](#resources)
- [Community](#community)

## Getting Started

### What is C#?
C# (pronounced "C-Sharp") is a modern, object-oriented programming language developed by Microsoft in 2000. It's part of the .NET ecosystem and combines the power of C++ with the simplicity of Visual Basic.

**Key Characteristics:**
- **Type-safe**: Prevents many common programming errors at compile time
- **Memory-managed**: Automatic garbage collection handles memory management
- **Cross-platform**: Runs on Windows, macOS, and Linux
- **Strongly typed**: Variables must be declared with specific types
- **Object-oriented**: Supports encapsulation, inheritance, and polymorphism

**Use Cases:**
- **Web Development**: ASP.NET Core for scalable web applications and APIs
- **Desktop Applications**: WPF, WinUI, and Avalonia for rich user interfaces
- **Mobile Development**: Xamarin and .NET MAUI for cross-platform apps
- **Game Development**: Unity engine uses C# as primary language
- **Cloud Services**: Azure Functions, microservices, and distributed systems
- **Machine Learning**: ML.NET for AI and data science applications
- **Enterprise Software**: Large-scale business applications and systems

### Prerequisites
- **Technical**: Basic computer literacy, understanding of file systems
- **Mathematical**: Basic algebra and logical thinking
- **Conceptual**: Problem-solving mindset and attention to detail
- **Optional but Helpful**: Previous programming experience in any language

## Learning Path

### Timeline Overview
- **Phase 1 (Foundations)**: 4-6 weeks - Basic syntax and OOP principles
- **Phase 2 (Intermediate)**: 6-8 weeks - Advanced features and .NET framework
- **Phase 3 (Advanced)**: 8-12 weeks - Professional development and specialization
- **Total Duration**: 18-26 weeks for comprehensive mastery

## Development Environment

### Essential Tools Setup

#### 1. Integrated Development Environments (IDEs)

**Visual Studio Community (Recommended for Beginners)**
- **Pros**: Full-featured, excellent debugging, IntelliSense, integrated testing
- **Cons**: Windows/Mac only, resource-intensive
- **Best for**: Comprehensive development, learning, enterprise projects
- **Installation**: Download from visualstudio.microsoft.com
- **Workloads to Install**: .NET desktop development, ASP.NET and web development

**Visual Studio Code (Lightweight Option)**
- **Pros**: Cross-platform, fast, extensible, free
- **Cons**: Requires extensions for full C# support
- **Best for**: Quick editing, cross-platform development
- **Essential Extensions**: C# Dev Kit, .NET Extension Pack, C# Extensions

**JetBrains Rider (Professional)**
- **Pros**: Excellent refactoring, cross-platform, advanced debugging
- **Cons**: Paid license, steep learning curve
- **Best for**: Professional development, advanced users

#### 2. .NET SDK Installation

**Understanding .NET Versions:**
- **.NET Framework**: Windows-only, legacy (4.8 is final version)
- **.NET Core**: Cross-platform, modern (merged into .NET 5+)
- **.NET 5+**: Unified platform (current: .NET 8, LTS versions: 6, 8)

**Installation Steps:**
```bash
# Check if .NET is installed
dotnet --version

# List installed SDKs
dotnet --list-sdks

# Create new project templates
dotnet new --list
```

#### 3. Essential Command Line Operations

**Project Management:**
```bash
# Create different project types
dotnet new console -n MyConsoleApp
dotnet new classlib -n MyLibrary
dotnet new webapi -n MyWebAPI
dotnet new mvc -n MyWebApp

# Solution management
dotnet new sln -n MySolution
dotnet sln add MyConsoleApp/MyConsoleApp.csproj
dotnet sln add MyLibrary/MyLibrary.csproj

# Package management
dotnet add package Newtonsoft.Json
dotnet remove package Newtonsoft.Json
dotnet restore

# Build and run
dotnet build
dotnet run
dotnet publish -c Release
```

## Phase 1: Foundations

### Week 1-2: Basic Syntax and Data Types

#### Variables and Data Types

**Value Types (Stored on Stack):**
```csharp
// Integral types
byte byteValue = 255;           // 0 to 255
sbyte sbyteValue = -128;        // -128 to 127
short shortValue = -32768;      // -32,768 to 32,767
ushort ushortValue = 65535;     // 0 to 65,535
int intValue = -2147483648;     // -2,147,483,648 to 2,147,483,647
uint uintValue = 4294967295;    // 0 to 4,294,967,295
long longValue = -9223372036854775808L;
ulong ulongValue = 18446744073709551615UL;

// Floating-point types
float floatValue = 3.14159F;    // ~7 digits precision
double doubleValue = 3.141592653589793; // ~15-17 digits precision
decimal decimalValue = 79228162514264337593543950335M; // 28-29 digits precision

// Character and boolean
char charValue = 'A';           // Single Unicode character
bool boolValue = true;          // true or false

// Date and time
DateTime dateTime = DateTime.Now;
DateOnly dateOnly = DateOnly.FromDateTime(DateTime.Now); // .NET 6+
TimeOnly timeOnly = TimeOnly.FromDateTime(DateTime.Now); // .NET 6+
```

**Reference Types (Stored on Heap):**
```csharp
// String (immutable reference type)
string stringValue = "Hello, World!";
string multilineString = @"This is a
multiline string";
string interpolatedString = $"The value is {intValue}";

// Arrays
int[] intArray = new int[5];                    // Fixed size array
int[] initializedArray = {1, 2, 3, 4, 5};     // Array literal
string[] stringArray = new string[] {"a", "b", "c"};

// Object
object objectValue = "Can hold any type";
object numberAsObject = 42;
```

**Nullable Types:**
```csharp
// Nullable value types
int? nullableInt = null;
DateTime? nullableDateTime = null;

// Null-coalescing operators
int result = nullableInt ?? 0;                 // Use 0 if null
string name = nullableString ??= "Default";   // Assign if null

// Null-conditional operators
int? length = nullableString?.Length;          // Safe navigation
string upper = nullableString?.ToUpper();     // Chain safely
```

**Type Conversion and Casting:**
```csharp
// Implicit conversion (safe, no data loss)
int intNum = 123;
double doubleNum = intNum;      // int to double

// Explicit conversion (potential data loss)
double pi = 3.14159;
int truncatedPi = (int)pi;      // Result: 3

// Parse methods
string numberString = "123";
int parsedInt = int.Parse(numberString);
int.TryParse("invalid", out int result); // Returns false if failed

// Convert class
int convertedInt = Convert.ToInt32("123");
string convertedString = Convert.ToString(123);
```

#### Constants and Readonly

```csharp
// Constants (compile-time constants)
const int MAX_SIZE = 100;
const string COMPANY_NAME = "Acme Corp";

// Readonly (runtime constants)
public class Configuration
{
    public readonly DateTime StartTime = DateTime.Now;
    public readonly string DatabaseConnection;
    
    public Configuration(string dbConnection)
    {
        DatabaseConnection = dbConnection; // Can only be set in constructor
    }
}

// Static readonly
public static readonly string ApplicationVersion = GetVersion();
```

#### Operators and Expressions

**Arithmetic Operators:**
```csharp
int a = 10, b = 3;
int addition = a + b;       // 13
int subtraction = a - b;    // 7
int multiplication = a * b; // 30
int division = a / b;       // 3 (integer division)
int modulus = a % b;        // 1 (remainder)

// Compound assignment
a += 5;  // a = a + 5
a -= 2;  // a = a - 2
a *= 2;  // a = a * 2
a /= 3;  // a = a / 3
a %= 4;  // a = a % 4

// Increment/Decrement
int x = 5;
int preIncrement = ++x;   // x becomes 6, returns 6
int postIncrement = x++;  // returns 6, then x becomes 7
```

**Comparison Operators:**
```csharp
int x = 10, y = 20;
bool equal = x == y;        // false
bool notEqual = x != y;     // true
bool greater = x > y;       // false
bool greaterEqual = x >= y; // false
bool less = x < y;          // true
bool lessEqual = x <= y;    // true
```

**Logical Operators:**
```csharp
bool a = true, b = false;
bool and = a && b;          // false (short-circuit evaluation)
bool or = a || b;           // true (short-circuit evaluation)
bool not = !a;              // false
bool xor = a ^ b;           // true (exclusive or)

// Bitwise operators
int x = 5;  // 101 in binary
int y = 3;  // 011 in binary
int bitwiseAnd = x & y;     // 1 (001)
int bitwiseOr = x | y;      // 7 (111)
int bitwiseXor = x ^ y;     // 6 (110)
int leftShift = x << 1;     // 10 (1010)
int rightShift = x >> 1;    // 2 (10)
```

### Week 2-3: Control Structures and Methods

#### Conditional Statements

**If-Else Statements:**
```csharp
int score = 85;

// Basic if-else
if (score >= 90)
{
    Console.WriteLine("Grade: A");
}
else if (score >= 80)
{
    Console.WriteLine("Grade: B");
}
else if (score >= 70)
{
    Console.WriteLine("Grade: C");
}
else if (score >= 60)
{
    Console.WriteLine("Grade: D");
}
else
{
    Console.WriteLine("Grade: F");
}

// Ternary operator
string result = score >= 60 ? "Pass" : "Fail";

// Pattern matching (C# 8+)
string grade = score switch
{
    >= 90 => "A",
    >= 80 => "B",
    >= 70 => "C",
    >= 60 => "D",
    _ => "F"
};
```

**Switch Statements:**
```csharp
// Traditional switch
DayOfWeek today = DateTime.Now.DayOfWeek;
switch (today)
{
    case DayOfWeek.Monday:
        Console.WriteLine("Start of work week");
        break;
    case DayOfWeek.Tuesday:
    case DayOfWeek.Wednesday:
    case DayOfWeek.Thursday:
        Console.WriteLine("Midweek");
        break;
    case DayOfWeek.Friday:
        Console.WriteLine("TGIF!");
        break;
    case DayOfWeek.Saturday:
    case DayOfWeek.Sunday:
        Console.WriteLine("Weekend!");
        break;
    default:
        Console.WriteLine("Unknown day");
        break;
}

// Switch expressions (C# 8+)
string dayType = today switch
{
    DayOfWeek.Monday or DayOfWeek.Tuesday or DayOfWeek.Wednesday 
        or DayOfWeek.Thursday or DayOfWeek.Friday => "Weekday",
    DayOfWeek.Saturday or DayOfWeek.Sunday => "Weekend",
    _ => "Unknown"
};

// Advanced pattern matching
object value = 42;
string description = value switch
{
    int i when i > 0 => "Positive integer",
    int i when i < 0 => "Negative integer",
    int => "Zero",
    string s when s.Length > 0 => "Non-empty string",
    string => "Empty string",
    null => "Null value",
    _ => "Unknown type"
};
```

#### Loops

**For Loops:**
```csharp
// Basic for loop
for (int i = 0; i < 10; i++)
{
    Console.WriteLine($"Iteration {i}");
}

// Nested loops
for (int row = 0; row < 3; row++)
{
    for (int col = 0; col < 3; col++)
    {
        Console.Write($"({row},{col}) ");
    }
    Console.WriteLine();
}

// Multiple variables
for (int i = 0, j = 10; i < j; i++, j--)
{
    Console.WriteLine($"i: {i}, j: {j}");
}
```

**While and Do-While Loops:**
```csharp
// While loop
int count = 0;
while (count < 5)
{
    Console.WriteLine($"Count: {count}");
    count++;
}

// Do-while loop (executes at least once)
string input;
do
{
    Console.Write("Enter 'quit' to exit: ");
    input = Console.ReadLine();
} while (input != "quit");

// Infinite loop with break
while (true)
{
    Console.Write("Enter a number (0 to exit): ");
    if (int.TryParse(Console.ReadLine(), out int number))
    {
        if (number == 0) break;
        Console.WriteLine($"You entered: {number}");
    }
    else
    {
        Console.WriteLine("Invalid input!");
        continue; // Skip rest of iteration
    }
}
```

**Foreach Loops:**
```csharp
// Array iteration
int[] numbers = {1, 2, 3, 4, 5};
foreach (int number in numbers)
{
    Console.WriteLine(number);
}

// String iteration
string text = "Hello";
foreach (char character in text)
{
    Console.WriteLine(character);
}

// Collection with index (using tuple deconstruction)
string[] names = {"Alice", "Bob", "Charlie"};
foreach ((string name, int index) in names.Select((name, index) => (name, index)))
{
    Console.WriteLine($"{index}: {name}");
}
```

#### Methods and Functions

**Basic Method Syntax:**
```csharp
// Method components: access modifier, return type, name, parameters
public static int AddNumbers(int a, int b)
{
    return a + b;
}

// Void method (no return value)
public static void PrintMessage(string message)
{
    Console.WriteLine(message);
}

// Method with multiple parameters
public static double CalculateArea(double length, double width)
{
    return length * width;
}

// Method overloading
public static int Add(int a, int b) => a + b;
public static double Add(double a, double b) => a + b;
public static string Add(string a, string b) => a + b;
```

**Parameter Types:**
```csharp
// Value parameters (default)
public static void ModifyValue(int x)
{
    x = 100; // Only local copy is modified
}

// Reference parameters
public static void ModifyReference(ref int x)
{
    x = 100; // Original variable is modified
}

// Output parameters
public static bool TryDivide(int dividend, int divisor, out int result)
{
    if (divisor != 0)
    {
        result = dividend / divisor;
        return true;
    }
    result = 0;
    return false;
}

// Parameter arrays
public static int Sum(params int[] numbers)
{
    return numbers.Sum();
}
// Usage: Sum(1, 2, 3, 4, 5) or Sum(new int[] {1, 2, 3})

// Optional parameters with default values
public static void CreateAccount(string name, string email, bool isActive = true, string role = "User")
{
    Console.WriteLine($"Creating account: {name}, {email}, Active: {isActive}, Role: {role}");
}
// Usage: CreateAccount("John", "john@email.com") or CreateAccount("Jane", "jane@email.com", false, "Admin")

// Named parameters
CreateAccount(email: "test@email.com", name: "Test User", role: "Guest");
```

**Expression-bodied Methods (C# 6+):**
```csharp
// Single expression methods
public static int Square(int x) => x * x;
public static string GetFullName(string first, string last) => $"{first} {last}";
public static bool IsEven(int number) => number % 2 == 0;

// Expression-bodied properties
public class Person
{
    public string FirstName { get; set; }
    public string LastName { get; set; }
    public string FullName => $"{FirstName} {LastName}";
    public bool IsAdult => Age >= 18;
    
    private int _age;
    public int Age
    {
        get => _age;
        set => _age = value < 0 ? 0 : value;
    }
}
```

**Local Functions (C# 7+):**
```csharp
public static int FactorialWithValidation(int n)
{
    if (n < 0)
        throw new ArgumentException("Number must be non-negative");
    
    return CalculateFactorial(n);
    
    // Local function
    int CalculateFactorial(int number)
    {
        if (number <= 1) return 1;
        return number * CalculateFactorial(number - 1);
    }
}
```

### Week 3-4: Object-Oriented Programming Fundamentals

#### Classes and Objects

**Basic Class Structure:**
```csharp
public class BankAccount
{
    // Fields (private data)
    private string _accountNumber;
    private decimal _balance;
    private string _ownerName;
    
    // Properties (public interface)
    public string AccountNumber 
    { 
        get { return _accountNumber; }
        private set { _accountNumber = value; } // Private setter
    }
    
    public decimal Balance 
    { 
        get { return _balance; }
        private set 
        { 
            if (value < 0)
                throw new ArgumentException("Balance cannot be negative");
            _balance = value; 
        }
    }
    
    public string OwnerName { get; set; }
    
    // Auto-implemented properties
    public DateTime CreatedDate { get; private set; }
    public AccountType Type { get; set; }
    
    // Constructors
    public BankAccount() // Default constructor
    {
        _accountNumber = GenerateAccountNumber();
        CreatedDate = DateTime.Now;
        Type = AccountType.Checking;
    }
    
    public BankAccount(string ownerName, decimal initialBalance) : this() // Constructor chaining
    {
        OwnerName = ownerName ?? throw new ArgumentNullException(nameof(ownerName));
        Balance = initialBalance;
    }
    
    public BankAccount(string ownerName, decimal initialBalance, AccountType type) 
        : this(ownerName, initialBalance)
    {
        Type = type;
    }
    
    // Methods
    public void Deposit(decimal amount)
    {
        if (amount <= 0)
            throw new ArgumentException("Deposit amount must be positive");
            
        Balance += amount;
        LogTransaction("Deposit", amount);
    }
    
    public bool Withdraw(decimal amount)
    {
        if (amount <= 0)
            throw new ArgumentException("Withdrawal amount must be positive");
            
        if (amount > Balance)
            return false; // Insufficient funds
            
        Balance -= amount;
        LogTransaction("Withdrawal", amount);
        return true;
    }
    
    public void Transfer(BankAccount targetAccount, decimal amount)
    {
        if (targetAccount == null)
            throw new ArgumentNullException(nameof(targetAccount));
            
        if (Withdraw(amount))
        {
            targetAccount.Deposit(amount);
            LogTransaction($"Transfer to {targetAccount.AccountNumber}", amount);
        }
        else
        {
            throw new InvalidOperationException("Insufficient funds for transfer");
        }
    }
    
    // Private helper methods
    private string GenerateAccountNumber()
    {
        return $"ACC{DateTime.Now.Ticks:X}";
    }
    
    private void LogTransaction(string type, decimal amount)
    {
        Console.WriteLine($"{DateTime.Now}: {type} of {amount:C} on account {AccountNumber}");
    }
    
    // Override ToString for better string representation
    public override string ToString()
    {
        return $"Account: {AccountNumber}, Owner: {OwnerName}, Balance: {Balance:C}, Type: {Type}";
    }
}

public enum AccountType
{
    Checking,
    Savings,
    Investment
}
```

**Object Initialization:**
```csharp
// Different ways to create objects
BankAccount account1 = new BankAccount();
BankAccount account2 = new BankAccount("John Doe", 1000.00m);
BankAccount account3 = new BankAccount("Jane Smith", 5000.00m, AccountType.Savings);

// Object initializer syntax
BankAccount account4 = new BankAccount
{
    OwnerName = "Alice Johnson",
    Type = AccountType.Investment
};

// Target-typed new (C# 9+)
BankAccount account5 = new("Bob Wilson", 2500.00m);
```

#### Encapsulation and Access Modifiers

**Access Modifiers:**
```csharp
public class AccessModifierExample
{
    public string PublicField;          // Accessible from anywhere
    protected string ProtectedField;    // Accessible from this class and derived classes
    internal string InternalField;     // Accessible within the same assembly
    protected internal string ProtectedInternalField; // Protected OR internal
    private protected string PrivateProtectedField;   // Protected AND internal (C# 7.2+)
    private string PrivateField;       // Only accessible within this class
    
    // Properties with different access levels
    public int PublicProperty { get; set; }
    public int ReadOnlyProperty { get; private set; }
    protected int ProtectedProperty { get; set; }
    internal int InternalProperty { get; set; }
    private int PrivateProperty { get; set; }
    
    // Mixed access levels for getters and setters
    public string Name { get; private set; }  // Public getter, private setter
    public int Age { get; protected set; }    // Public getter, protected setter
}
```

**Property Patterns:**
```csharp
public class Person
{
    private string _firstName;
    private string _lastName;
    private int _age;
    
    // Full property implementation
    public string FirstName
    {
        get { return _firstName; }
        set 
        { 
            if (string.IsNullOrWhiteSpace(value))
                throw new ArgumentException("First name cannot be empty");
            _firstName = value.Trim(); 
        }
    }
    
    // Auto-implemented property
    public string LastName { get; set; }
    
    // Read-only property
    public string FullName => $"{FirstName} {LastName}";
    
    // Property with validation
    public int Age
    {
        get => _age;
        set
        {
            if (value < 0 || value > 150)
                throw new ArgumentOutOfRangeException(nameof(value), "Age must be between 0 and 150");
            _age = value;
        }
    }
    
    // Computed property
    public bool IsAdult => Age >= 18;
    
    // Property with lazy initialization
    private List<string> _hobbies;
    public List<string> Hobbies => _hobbies ??= new List<string>();
}
```

#### Inheritance

**Base Class and Derived Classes:**
```csharp
// Base class
public abstract class Vehicle
{
    // Protected members accessible to derived classes
    protected string _make;
    protected string _model;
    protected int _year;
    
    // Public properties
    public string Make => _make;
    public string Model => _model;
    public int Year => _year;
    public bool IsRunning { get; protected set; }
    
    // Constructor
    protected Vehicle(string make, string model, int year)
    {
        _make = make ?? throw new ArgumentNullException(nameof(make));
        _model = model ?? throw new ArgumentNullException(nameof(model));
        _year = year;
    }
    
    // Virtual methods (can be overridden)
    public virtual void Start()
    {
        if (!IsRunning)
        {
            IsRunning = true;
            Console.WriteLine($"{Make} {Model} is starting...");
        }
    }
    
    public virtual void Stop()
    {
        if (IsRunning)
        {
            IsRunning = false;
            Console.WriteLine($"{Make} {Model} has stopped.");
        }
    }
    
    // Abstract methods (must be implemented by derived classes)
    public abstract void Accelerate();
    public abstract void Brake();
    public abstract int GetMaxSpeed();
    
    // Sealed method (cannot be overridden further)
    public sealed override string ToString()
    {
        return $"{Year} {Make} {Model}";
    }
}

// Derived class - Car
public class Car : Vehicle
{
    public int NumberOfDoors { get; set; }
    public string FuelType { get; set; }
    
    public Car(string make, string model, int year, int doors, string fuelType) 
        : base(make, model, year)
    {
        NumberOfDoors = doors;
        FuelType = fuelType;
    }
    
    // Override abstract methods
    public override void Accelerate()
    {
        if (IsRunning)
            Console.WriteLine($"{Make} {Model} is accelerating smoothly...");
        else
            Console.WriteLine("Cannot accelerate. Car is not running.");
    }
    
    public override void Brake()
    {
        Console.WriteLine($"{Make} {Model} is braking with ABS...");
    }
    
    public override int GetMaxSpeed()
    {
        return FuelType.ToLower() switch
        {
            "electric" => 200,
            "hybrid" => 180,
            "gasoline" => 160,
            "diesel" => 140,
            _ => 120
        };
    }
    
    // Override virtual method
    public override void Start()
    {
        base.Start(); // Call base implementation
        Console.WriteLine("Car systems initialized.");
    }
    
    // New method specific to Car
    public void OpenTrunk()
    {
        Console.WriteLine("Trunk opened.");
    }
}

// Another derived class - Motorcycle
public class Motorcycle : Vehicle
{
    public int EngineCC { get; set; }
    public bool HasSidecar { get; set; }
    
    public Motorcycle(string make, string model, int year, int engineCC, bool hasSidecar = false) 
        : base(make, model, year)
    {
        EngineCC = engineCC;
        HasSidecar = hasSidecar;
    }
    
    public override void Accelerate()
    {
        if (IsRunning)
            Console.WriteLine($"{Make} {Model} is accelerating rapidly!");
        else
            Console.WriteLine("Cannot accelerate. Motorcycle is not running.");
    }
    
    public override void Brake()
    {
        Console.WriteLine($"{Make} {Model} is braking - lean into the turn!");
    }
    
    public override int GetMaxSpeed()
    {
        return EngineCC switch
        {
            <= 125 => 80,
            <= 250 => 120,
            <= 600 => 180,
            <= 1000 => 250,
            _ => 300
        };
    }
    
    public void Wheelie()
    {
        if (IsRunning && !HasSidecar)
            Console.WriteLine("Performing a wheelie!");
        else
            Console.WriteLine("Cannot perform wheelie.");
    }
}
```

**Inheritance Usage:**
```csharp
// Polymorphism in action
List<Vehicle> vehicles = new List<Vehicle>
{
    new Car("Toyota", "Camry", 2023, 4, "hybrid"),
    new Car("Tesla", "Model 3", 2023, 4, "electric"),
    new Motorcycle("Harley-Davidson", "Sportster", 2023, 883),
    new Motorcycle("Honda", "CBR600RR", 2023, 600)
};

foreach (Vehicle vehicle in vehicles)
{
    Console.WriteLine(vehicle); // Calls overridden ToString
    vehicle.Start();           // Calls appropriate Start method
    vehicle.Accelerate();      // Calls overridden Accelerate method
    Console.WriteLine($"Max Speed: {vehicle.GetMaxSpeed()} km/h");
    
    // Type checking and casting
    if (vehicle is Car car)
    {
        car.OpenTrunk();
        Console.WriteLine($"Doors: {car.NumberOfDoors}, Fuel: {car.FuelType}");
    }
    else if (vehicle is Motorcycle motorcycle)
    {
        motorcycle.Wheelie();
        Console.WriteLine($"Engine: {motorcycle.EngineCC}cc, Sidecar: {motorcycle.HasSidecar}");
    }
    
    vehicle.Stop();
    Console.WriteLine();
}
```

#### Polymorphism

**Method Overriding vs Method Hiding:**
```csharp
public class BaseClass
{
    public virtual void VirtualMethod()
    {
        Console.WriteLine("Base virtual method");
    }
    
    public void NonVirtualMethod()
    {
        Console.WriteLine("Base non-virtual method");
    }
}

public class DerivedClass : BaseClass
{
    // Method overriding (polymorphic)
    public override void VirtualMethod()
    {
        Console.WriteLine("Derived override method");
    }
    
    // Method hiding (non-polymorphic)
    public new void NonVirtualMethod()
    {
        Console.WriteLine("Derived new method");
    }
}

// Demonstration
BaseClass baseRef = new DerivedClass();
baseRef.VirtualMethod();    // Output: "Derived override method" (polymorphic)
baseRef.NonVirtualMethod(); // Output: "Base non-virtual method" (not polymorphic)

DerivedClass derivedRef = new DerivedClass();
derivedRef.VirtualMethod();    // Output: "Derived override method"
derivedRef.NonVirtualMethod(); // Output: "Derived new method"
```

#### Interfaces

**Interface Definition and Implementation:**
```csharp
// Interface definition
public interface IDrawable
{
    void Draw();
    void Move(int x, int y);
    
    // Properties in interfaces
    string Color { get; set; }
    bool IsVisible { get; }
    
    // Default interface methods (C# 8+)
    void Hide() => Console.WriteLine("Object is now hidden");
    
    // Static interface methods (C# 11+)
    static abstract void Reset();
}

// Multiple interface inheritance
public interface IResizable
{
    void Resize(double factor);
    double Width { get; set; }
    double Height { get; set; }
}

public interface IRotatable
{
    void Rotate(double angle);
    double Rotation { get; set; }
}

// Class implementing multiple interfaces
public class Shape : IDrawable, IResizable, IRotatable
{
    public string Color { get; set; } = "Black";
    public bool IsVisible { get; private set; } = true;
    public double Width { get; set; }
    public double Height { get; set; }
    public double Rotation { get; set; }
    
    protected double X { get; set; }
    protected double Y { get; set; }
    
    public virtual void Draw()
    {
        if (IsVisible)
            Console.WriteLine($"Drawing {GetType().Name} at ({X}, {Y}) with color {Color}");
    }
    
    public void Move(int x, int y)
    {
        X = x;
        Y = y;
        Console.WriteLine($"Moved to ({X}, {Y})");
    }
    
    public virtual void Resize(double factor)
    {
        Width *= factor;
        Height *= factor;
        Console.WriteLine($"Resized by factor {factor}. New size: {Width}x{Height}");
    }
    
    public virtual void Rotate(double angle)
    {
        Rotation += angle;
        Console.WriteLine($"Rotated by {angle} degrees. Total rotation: {Rotation}");
    }
    
    // Override default interface method
    public new void Hide()
    {
        IsVisible = false;
        Console.WriteLine($"{GetType().Name} is now hidden");
    }
    
    public static void Reset()
    {
        Console.WriteLine("Shape reset to default state");
    }
}

// Explicit interface implementation
public class Rectangle : Shape
{
    // Explicit implementation (only accessible through interface reference)
    void IDrawable.Draw()
    {
        Console.WriteLine($"Drawing rectangle explicitly: {Width}x{Height}");
    }
    
    // Public implementation
    public override void Draw()
    {
        Console.WriteLine($"Drawing rectangle: {Width}x{Height} at ({X}, {Y})");
    }
}

// Usage examples
Rectangle rect = new Rectangle { Width = 10, Height = 5, Color = "Red" };
rect.Draw(); // Calls public Draw method

IDrawable drawable = rect;
drawable.Draw(); // Calls explicit implementation
```

**Abstract Classes vs Interfaces:**
```csharp
// Abstract class - provides base implementation
public abstract class Animal
{
    public string Name { get; set; }
    public int Age { get; set; }
    
    // Concrete method
    public void Sleep()
    {
        Console.WriteLine($"{Name} is sleeping");
    }
    
    // Abstract method - must be implemented
    public abstract void MakeSound();
    
    // Virtual method - can be overridden
    public virtual void Eat()
    {
        Console.WriteLine($"{Name} is eating");
    }
}

// Interface - defines contract
public interface IPet
{
    string Owner { get; set; }
    void Play();
    void ShowAffection();
}

// Class inheriting from abstract class and implementing interface
public class Dog : Animal, IPet
{
    public string Owner { get; set; }
    public string Breed { get; set; }
    
    public override void MakeSound()
    {
        Console.WriteLine($"{Name} barks: Woof! Woof!");
    }
    
    public override void Eat()
    {
        Console.WriteLine($"{Name} is eating dog food enthusiastically");
    }
    
    public void Play()
    {
        Console.WriteLine($"{Name} is playing fetch");
    }
    
    public void ShowAffection()
    {
        Console.WriteLine($"{Name} is wagging tail and licking {Owner}");
    }
    
    // Dog-specific method
    public void Fetch(string item)
    {
        Console.WriteLine($"{Name} is fetching the {item}");
    }
}
```

### Week 4: Collections and Arrays

#### Arrays Deep Dive

**Single-dimensional Arrays:**
```csharp
// Array declaration and initialization
int[] numbers = new int[5];                    // Creates array with 5 elements (all 0)
int[] values = {1, 2, 3, 4, 5};               // Array literal
int[] scores = new int[] {95, 87, 92, 78, 88}; // Explicit initialization
string[] names = new string[3] {"Alice", "Bob", "Charlie"}; // Mixed syntax

// Array access and modification
numbers[0] = 10;
numbers[1] = 20;
int firstNumber = numbers[0];

// Array properties and methods
int length = numbers.Length;
int lastIndex = numbers.Length - 1;

// Array iteration
for (int i = 0; i < numbers.Length; i++)
{
    Console.WriteLine($"numbers[{i}] = {numbers[i]}");
}

foreach (int number in numbers)
{
    Console.WriteLine(number);
}

// Array methods
Array.Sort(scores);                    // Sort in-place
Array.Reverse(scores);                 // Reverse in-place
int index = Array.IndexOf(scores, 92); // Find index of value
bool contains = Array.Exists(scores, s => s > 90); // Check condition

// Array copying
int[] copy1 = new int[scores.Length];
Array.Copy(scores, copy1, scores.Length);

int[] copy2 = (int[])scores.Clone();   // Shallow copy
int[] copy3 = scores.ToArray();        // Using LINQ
```

**Multi-dimensional Arrays:**
```csharp
// Two-dimensional array
int[,] matrix = new int[3, 4];         // 3 rows, 4 columns
int[,] grid = {{1, 2, 3}, {4, 5, 6}, {7, 8, 9}};

// Access elements
matrix[0, 0] = 10;
matrix[1, 2] = 20;
int value = grid[2, 1]; // Gets 8

// Get dimensions
int rows = matrix.GetLength(0);        // 3
int cols = matrix.GetLength(1);        // 4

// Iterate through 2D array
for (int i = 0; i < grid.GetLength(0); i++)
{
    for (int j = 0; j < grid.GetLength(1); j++)
    {
        Console.Write($"{grid[i, j]} ");
    }
    Console.WriteLine();
}

// Three-dimensional array
int[,,] cube = new int[2, 3, 4];      // 2x3x4 cube
cube[1, 2, 3] = 100;
```

**Jagged Arrays:**
```csharp
// Jagged array (array of arrays)
int[][] jaggedArray = new int[3][];
jaggedArray[0] = new int[4] {1, 2, 3, 4};
jaggedArray[1] = new int[2] {5, 6};
jaggedArray[2] = new int[3] {7, 8, 9};

// Alternative initialization
int[][] scores = 
{
    new int[] {95, 87, 92},
    new int[] {78, 88, 91, 85},
    new int[] {82, 94}
};

// Access jagged array
for (int i = 0; i < scores.Length; i++)
{
    Console.Write($"Student {i + 1}: ");
    for (int j = 0; j < scores[i].Length; j++)
    {
        Console.Write($"{scores[i][j]} ");
    }
    Console.WriteLine();
}
```

#### Generic Collections

**List<T> - Dynamic Arrays:**
```csharp
// List creation and initialization
List<int> numbers = new List<int>();
List<string> names = new List<string> {"Alice", "Bob", "Charlie"};
List<int> scores = new List<int>(10); // Initial capacity of 10

// Adding elements
numbers.Add(10);
numbers.Add(20);
numbers.AddRange(new int[] {30, 40, 50});
numbers.Insert(1, 15); // Insert at index 1

// Accessing elements
int first = numbers[0];
int last = numbers[numbers.Count - 1];

// Removing elements
numbers.Remove(20);        // Remove first occurrence of 20
numbers.RemoveAt(0);       // Remove element at index 0
numbers.RemoveAll(n => n > 25); // Remove all elements > 25
numbers.Clear();           // Remove all elements

// List methods
names.Sort();                           // Sort alphabetically
names.Reverse();                        // Reverse order
bool contains = names.Contains("Alice"); // Check if contains
int index = names.IndexOf("Bob");       // Find index
string found = names.Find(n => n.StartsWith("C")); // Find first match
List<string> filtered = names.FindAll(n => n.Length > 3); // Find all matches

// Converting
string[] nameArray = names.ToArray();
string joined = string.Join(", ", names);

// LINQ with Lists
var longNames = names.Where(n => n.Length > 4).ToList();
var upperNames = names.Select(n => n.ToUpper()).ToList();
bool anyStartsWithA = names.Any(n => n.StartsWith("A"));
```

**Dictionary<TKey, TValue> - Key-Value Pairs:**
```csharp
// Dictionary creation and initialization
Dictionary<string, int> ages = new Dictionary<string, int>();
Dictionary<int, string> students = new Dictionary<int, string>
{
    {1, "Alice"},
    {2, "Bob"},
    {3, "Charlie"}
};

// Collection initializer (C# 6+)
Dictionary<string, string> capitals = new Dictionary<string, string>
{
    ["USA"] = "Washington",
    ["France"] = "Paris",
    ["Japan"] = "Tokyo"
};

// Adding and updating
ages["Alice"] = 25;
ages["Bob"] = 30;
ages.Add("Charlie", 28);

// Safe adding
if (!ages.ContainsKey("David"))
{
    ages["David"] = 35;
}

// TryAdd (returns false if key exists)
bool added = ages.TryAdd("Eve", 22);

// Accessing values
int aliceAge = ages["Alice"];

// Safe accessing
if (ages.TryGetValue("Frank", out int frankAge))
{
    Console.WriteLine($"Frank is {frankAge} years old");
}
else
{
    Console.WriteLine("Frank not found");
}

// Removing
ages.Remove("Bob");
bool removed = ages.Remove("NonExistent"); // Returns false

// Iteration
foreach (KeyValuePair<string, int> kvp in ages)
{
    Console.WriteLine($"{kvp.Key}: {kvp.Value}");
}

foreach (string name in ages.Keys)
{
    Console.WriteLine($"Name: {name}");
}

foreach (int age in ages.Values)
{
    Console.WriteLine($"Age: {age}");
}

// Dictionary methods
bool hasKey = ages.ContainsKey("Alice");
bool hasValue = ages.ContainsValue(25);
```

**HashSet<T> - Unique Collections:**
```csharp
// HashSet creation
HashSet<string> uniqueNames = new HashSet<string>();
HashSet<int> numbers = new HashSet<int> {1, 2, 3, 4, 5};

// Adding elements (duplicates ignored)
uniqueNames.Add("Alice");
uniqueNames.Add("Bob");
uniqueNames.Add("Alice"); // Ignored - already exists

// Set operations
HashSet<int> set1 = new HashSet<int> {1, 2, 3, 4, 5};
HashSet<int> set2 = new HashSet<int> {4, 5, 6, 7, 8};

// Union (combines both sets)
HashSet<int> union = new HashSet<int>(set1);
union.UnionWith(set2); // {1, 2, 3, 4, 5, 6, 7, 8}

// Intersection (common elements)
HashSet<int> intersection = new HashSet<int>(set1);
intersection.IntersectWith(set2); // {4, 5}

// Difference (elements in set1 but not in set2)
HashSet<int> difference = new HashSet<int>(set1);
difference.ExceptWith(set2); // {1, 2, 3}

// Symmetric difference (elements in either set but not both)
HashSet<int> symmetricDiff = new HashSet<int>(set1);
symmetricDiff.SymmetricExceptWith(set2); // {1, 2, 3, 6, 7, 8}

// Set comparisons
bool isSubset = set1.IsSubsetOf(set2);
bool isSuperset = set1.IsSupersetOf(set2);
bool overlaps = set1.Overlaps(set2);
```

**Queue<T> and Stack<T>:**
```csharp
// Queue (FIFO - First In, First Out)
Queue<string> queue = new Queue<string>();
queue.Enqueue("First");
queue.Enqueue("Second");
queue.Enqueue("Third");

string first = queue.Dequeue(); // "First"
string next = queue.Peek();     // "Second" (doesn't remove)
int count = queue.Count;        // 2

// Stack (LIFO - Last In, First Out)
Stack<int> stack = new Stack<int>();
stack.Push(10);
stack.Push(20);
stack.Push(30);

int top = stack.Pop();  // 30
int peek = stack.Peek(); // 20 (doesn't remove)
bool empty = stack.Count == 0; // false
```

## Phase 2: Intermediate

### Week 5-6: Exception Handling and File I/O

#### Exception Handling Deep Dive

**Exception Hierarchy and Types:**
```csharp
// Common exception types
try
{
    // ArgumentException family
    throw new ArgumentNullException("parameter", "Parameter cannot be null");
    throw new ArgumentOutOfRangeException("index", "Index was out of range");
    throw new ArgumentException("Invalid argument provided");
    
    // InvalidOperationException
    throw new InvalidOperationException("Operation not valid in current state");
    
    // NotSupportedException
    throw new NotSupportedException("This operation is not supported");
    
    // FormatException
    int number = int.Parse("invalid"); // Throws FormatException
    
    // OverflowException
    checked
    {
        int max = int.MaxValue;
        int overflow = max + 1; // Throws OverflowException
    }
}
catch (ArgumentNullException ex)
{
    Console.WriteLine($"Null argument: {ex.ParamName} - {ex.Message}");
}
catch (ArgumentOutOfRangeException ex)
{
    Console.WriteLine($"Out of range: {ex.ParamName} - {ex.Message}");
}
catch (ArgumentException ex) // Catches remaining ArgumentException types
{
    Console.WriteLine($"Argument error: {ex.Message}");
}
catch (FormatException ex)
{
    Console.WriteLine($"Format error: {ex.Message}");
}
catch (OverflowException ex)
{
    Console.WriteLine($"Overflow error: {ex.Message}");
}
catch (Exception ex) // Catch-all for any other exceptions
{
    Console.WriteLine($"Unexpected error: {ex.GetType().Name} - {ex.Message}");
    Console.WriteLine($"Stack trace: {ex.StackTrace}");
}
finally
{
    Console.WriteLine("Cleanup code executed regardless of exceptions");
}
```

**Custom Exceptions:**
```csharp
// Custom exception class
public class InsufficientFundsException : Exception
{
    public decimal CurrentBalance { get; }
    public decimal RequestedAmount { get; }
    
    public InsufficientFundsException() : base() { }
    
    public InsufficientFundsException(string message) : base(message) { }
    
    public InsufficientFundsException(string message, Exception innerException) 
        : base(message, innerException) { }
    
    public InsufficientFundsException(decimal currentBalance, decimal requestedAmount)
        : base($"Insufficient funds. Balance: {currentBalance:C}, Requested: {requestedAmount:C}")
    {
        CurrentBalance = currentBalance;
        RequestedAmount = requestedAmount;
    }
}

// Usage of custom exception
public class BankAccount
{
    private decimal _balance;
    
    public void Withdraw(decimal amount)
    {
        if (amount > _balance)
        {
            throw new InsufficientFundsException(_balance, amount);
        }
        _balance -= amount;
    }
}

// Handling custom exception
try
{
    var account = new BankAccount();
    account.Withdraw(1000);
}
catch (InsufficientFundsException ex)
{
    Console.WriteLine($"Cannot withdraw: {ex.Message}");
    Console.WriteLine($"Current balance: {ex.CurrentBalance:C}");
    Console.WriteLine($"Requested amount: {ex.RequestedAmount:C}");
}
```

**Exception Filtering and Advanced Patterns:**
```csharp
// Exception filters (C# 6+)
try
{
    ProcessData();
}
catch (HttpRequestException ex) when (ex.Message.Contains("timeout"))
{
    Console.WriteLine("Request timed out, retrying...");
    // Retry logic
}
catch (HttpRequestException ex) when (ex.Message.Contains("404"))
{
    Console.WriteLine("Resource not found");
}
catch (HttpRequestException ex)
{
    Console.WriteLine($"HTTP error: {ex.Message}");
}

// Nested try-catch
try
{
    try
    {
        RiskyOperation();
    }
    catch (SpecificException ex)
    {
        // Handle specific exception locally
        LogError(ex);
        throw; // Re-throw to outer catch
    }
}
catch (Exception ex)
{
    // Handle all exceptions at higher level
    Console.WriteLine($"Operation failed: {ex.Message}");
}

// Exception aggregation
List<Exception> exceptions = new List<Exception>();
foreach (var item in items)
{
    try
    {
        ProcessItem(item);
    }
    catch (Exception ex)
    {
        exceptions.Add(ex);
    }
}

if (exceptions.Any())
{
    throw new AggregateException("Multiple errors occurred", exceptions);
}
```

#### File I/O Operations

**File Reading and Writing:**
```csharp
// Simple file operations
string filePath = @"C:\temp\example.txt";

// Write to file
File.WriteAllText(filePath, "Hello, World!");
File.WriteAllLines(filePath, new string[] {"Line 1", "Line 2", "Line 3"});

// Append to file
File.AppendAllText(filePath, "\nAppended text");

// Read from file
string content = File.ReadAllText(filePath);
string[] lines = File.ReadAllLines(filePath);

// File information
if (File.Exists(filePath))
{
    FileInfo info = new FileInfo(filePath);
    Console.WriteLine($"Size: {info.Length} bytes");
    Console.WriteLine($"Created: {info.CreationTime}");
    Console.WriteLine($"Modified: {info.LastWriteTime}");
    Console.WriteLine($"Directory: {info.DirectoryName}");
}

// Stream-based operations for large files
using (StreamWriter writer = new StreamWriter(filePath))
{
    writer.WriteLine("Line 1");
    writer.WriteLine("Line 2");
    writer.Flush(); // Ensure data is written
}

using (StreamReader reader = new StreamReader(filePath))
{
    string line;
    while ((line = reader.ReadLine()) != null)
    {
        Console.WriteLine(line);
    }
}
```

**Advanced File Operations:**
```csharp
// Binary file operations
byte[] data = {0x48, 0x65, 0x6C, 0x6C, 0x6F}; // "Hello" in ASCII
File.WriteAllBytes("binary.dat", data);

byte[] readData = File.ReadAllBytes("binary.dat");
string text = Encoding.ASCII.GetString(readData);

// Memory-mapped files for large data
using (var mmf = MemoryMappedFile.CreateFromFile("largefile.dat"))
using (var accessor = mmf.CreateViewAccessor())
{
    // Read/write directly to memory-mapped region
    byte value = accessor.ReadByte(0);
    accessor.Write(0, (byte)255);
}

// Asynchronous file operations
async Task ReadFileAsync(string path)
{
    using (StreamReader reader = new StreamReader(path))
    {
        string content = await reader.ReadToEndAsync();
        Console.WriteLine(content);
    }
}

async Task WriteFileAsync(string path, string content)
{
    using (StreamWriter writer = new StreamWriter(path))
    {
        await writer.WriteAsync(content);
    }
}
```

**Directory Operations:**
```csharp
string directoryPath = @"C:\temp\example";

// Create directory
Directory.CreateDirectory(directoryPath);

// Check if directory exists
if (Directory.Exists(directoryPath))
{
    // Get directory information
    DirectoryInfo dirInfo = new DirectoryInfo(directoryPath);
    
    // Get files and subdirectories
    FileInfo[] files = dirInfo.GetFiles();
    DirectoryInfo[] subdirs = dirInfo.GetDirectories();
    
    // Get files with pattern
    FileInfo[] txtFiles = dirInfo.GetFiles("*.txt");
    FileInfo[] allFiles = dirInfo.GetFiles("*.*", SearchOption.AllDirectories);
    
    // Enumerate files (memory efficient for large directories)
    foreach (string file in Directory.EnumerateFiles(directoryPath, "*.log"))
    {
        Console.WriteLine(file);
    }
}

// Path operations
string combined = Path.Combine(directoryPath, "subfolder", "file.txt");
string fileName = Path.GetFileName(combined);
string directory = Path.GetDirectoryName(combined);
string extension = Path.GetExtension(combined);
string withoutExtension = Path.GetFileNameWithoutExtension(combined);

// Temporary files
string tempFile = Path.GetTempFileName();
string tempPath = Path.GetTempPath();
```

**File Watching:**
```csharp
// Monitor file system changes
FileSystemWatcher watcher = new FileSystemWatcher(@"C:\temp");
watcher.NotifyFilter = NotifyFilters.CreationTime | NotifyFilters.LastWrite 
                     | NotifyFilters.FileName | NotifyFilters.DirectoryName;

watcher.Filter = "*.txt";
watcher.IncludeSubdirectories = true;

watcher.Created += OnFileCreated;
watcher.Changed += OnFileChanged;
watcher.Deleted += OnFileDeleted;
watcher.Renamed += OnFileRenamed;

watcher.EnableRaisingEvents = true;

void OnFileCreated(object sender, FileSystemEventArgs e)
{
    Console.WriteLine($"File created: {e.FullPath}");
}

void OnFileChanged(object sender, FileSystemEventArgs e)
{
    Console.WriteLine($"File changed: {e.FullPath}");
}

void OnFileDeleted(object sender, FileSystemEventArgs e)
{
    Console.WriteLine($"File deleted: {e.FullPath}");
}

void OnFileRenamed(object sender, RenamedEventArgs e)
{
    Console.WriteLine($"File renamed from {e.OldFullPath} to {e.FullPath}");
}
```

### Week 7-8: Generics and LINQ

#### Generics Deep Dive

**Generic Classes:**
```csharp
// Generic class with single type parameter
public class GenericRepository<T> where T : class
{
    private List<T> _items = new List<T>();
    
    public void Add(T item)
    {
        if (item != null)
            _items.Add(item);
    }
    
    public T GetById(int id) where T : IIdentifiable
    {
        return _items.FirstOrDefault(item => item.Id == id);
    }
    
    public IEnumerable<T> GetAll()
    {
        return _items.AsReadOnly();
    }
    
    public bool Remove(T item)
    {
        return _items.Remove(item);
    }
    
    public int Count => _items.Count;
}

// Generic class with multiple type parameters
public class KeyValueStore<TKey, TValue> 
    where TKey : IEquatable<TKey>
    where TValue : class
{
    private Dictionary<TKey, TValue> _store = new Dictionary<TKey, TValue>();
    
    public void Set(TKey key, TValue value)
    {
        _store[key] = value;
    }
    
    public TValue Get(TKey key)
    {
        return _store.TryGetValue(key, out TValue value) ? value : null;
    }
    
    public bool TryGet(TKey key, out TValue value)
    {
        return _store.TryGetValue(key, out value);
    }
}

// Generic constraints examples
public class ConstraintExamples
{
    // Reference type constraint
    public class ReferenceTypeContainer<T> where T : class
    {
        public T Value { get; set; }
    }
    
    // Value type constraint
    public class ValueTypeContainer<T> where T : struct
    {
        public T Value { get; set; }
        public T? NullableValue { get; set; }
    }
    
    // Constructor constraint
    public class ConstructorConstraint<T> where T : new()
    {
        public T CreateInstance()
        {
            return new T();
        }
    }
    
    // Interface constraint
    public class ComparableContainer<T> where T : IComparable<T>
    {
        public T Max(T a, T b)
        {
            return a.CompareTo(b) > 0 ? a : b;
        }
    }
    
    // Base class constraint
    public class AnimalContainer<T> where T : Animal
    {
        public void MakeSound(T animal)
        {
            animal.MakeSound();
        }
    }
    
    // Multiple constraints
    public class ComplexConstraint<T> 
        where T : class, IDisposable, IComparable<T>, new()
    {
        public T CreateAndCompare(T other)
        {
            T instance = new T();
            return instance.CompareTo(other) > 0 ? instance : other;
        }
    }
}
```

**Generic Methods:**
```csharp
public static class GenericMethods
{
    // Generic method with type inference
    public static void Swap<T>(ref T a, ref T b)
    {
        T temp = a;
        a = b;
        b = temp;
    }
    
    // Generic method with constraints
    public static T FindMax<T>(IEnumerable<T> items) where T : IComparable<T>
    {
        if (!items.Any())
            throw new ArgumentException("Collection cannot be empty");
            
        T max = items.First();
        foreach (T item in items.Skip(1))
        {
            if (item.CompareTo(max) > 0)
                max = item;
        }
        return max;
    }
    
    // Generic method with multiple type parameters
    public static TResult Transform<TInput, TResult>(TInput input, Func<TInput, TResult> transformer)
    {
        return transformer(input);
    }
    
    // Generic method with complex constraints
    public static void ProcessItems<T>(IEnumerable<T> items, Action<T> processor) 
        where T : IDisposable
    {
        foreach (T item in items)
        {
            try
            {
                processor(item);
            }
            finally
            {
                item?.Dispose();
            }
        }
    }
}

// Usage examples
int a = 5, b = 10;
GenericMethods.Swap(ref a, ref b); // Type inferred as int

List<int> numbers = new List<int> {3, 7, 2, 9, 1};
int max = GenericMethods.FindMax(numbers);

string result = GenericMethods.Transform(42, x => $"Number: {x}");
```

**Covariance and Contravariance:**
```csharp
// Covariance (out keyword) - can return more derived types
public interface ICovariant<out T>
{
    T GetItem();
    // T cannot be used as input parameter in covariant interface
}

public class CovariantImpl<T> : ICovariant<T>
{
    private T _item;
    
    public CovariantImpl(T item)
    {
        _item = item;
    }
    
    public T GetItem()
    {
        return _item;
    }
}

// Contravariance (in keyword) - can accept more base types
public interface IContravariant<in T>
{
    void ProcessItem(T item);
    // T cannot be used as return type in contravariant interface
}

public class ContravariantImpl<T> : IContravariant<T>
{
    public void ProcessItem(T item)
    {
        Console.WriteLine($"Processing: {item}");
    }
}

// Usage examples
ICovariant<string> stringCovariant = new CovariantImpl<string>("Hello");
ICovariant<object> objectCovariant = stringCovariant; // Valid due to covariance

IContravariant<object> objectContravariant = new ContravariantImpl<object>();
IContravariant<string> stringContravariant = objectContravariant; // Valid due to contravariance
```

#### LINQ (Language Integrated Query)

**Query Syntax vs Method Syntax:**
```csharp
List<Person> people = new List<Person>
{
    new Person { Name = "Alice", Age = 25, City = "New York" },
    new Person { Name = "Bob", Age = 30, City = "London" },
    new Person { Name = "Charlie", Age = 35, City = "New York" },
    new Person { Name = "Diana", Age = 28, City = "Paris" }
};

// Query syntax
var queryResult = from p in people
                  where p.Age > 25
                  orderby p.Name
                  select new { p.Name, p.Age };

// Method syntax (equivalent)
var methodResult = people
    .Where(p => p.Age > 25)
    .OrderBy(p => p.Name)
    .Select(p => new { p.Name, p.Age });

// Complex query with grouping
var groupedQuery = from p in people
                   group p by p.City into cityGroup
                   where cityGroup.Count() > 1
                   select new 
                   { 
                       City = cityGroup.Key, 
                       Count = cityGroup.Count(),
                       AverageAge = cityGroup.Average(x => x.Age)
                   };

// Method syntax equivalent
var groupedMethod = people
    .GroupBy(p => p.City)
    .Where(g => g.Count() > 1)
    .Select(g => new 
    { 
        City = g.Key, 
        Count = g.Count(),
        AverageAge = g.Average(x => x.Age)
    });
```

**LINQ Standard Query Operators:**
```csharp
List<int> numbers = new List<int> {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
List<string> words = new List<string> {"apple", "banana", "cherry", "date", "elderberry"};

// Filtering
var evenNumbers = numbers.Where(n => n % 2 == 0);
var longWords = words.Where(w => w.Length > 5);
var firstThreeEvens = numbers.Where(n => n % 2 == 0).Take(3);
var skipFirstTwo = numbers.Skip(2);
var takeWhileLessThan6 = numbers.TakeWhile(n => n < 6);
var skipWhileLessThan5 = numbers.SkipWhile(n => n < 5);

// Projection
var squares = numbers.Select(n => n * n);
var wordLengths = words.Select(w => w.Length);
var wordInfo = words.Select((word, index) => new { Index = index, Word = word, Length = word.Length });

// SelectMany for flattening
List<List<int>> nestedLists = new List<List<int>>
{
    new List<int> {1, 2, 3},
    new List<int> {4, 5, 6},
    new List<int> {7, 8, 9}
};
var flattened = nestedLists.SelectMany(list => list);

// Ordering
var ascending = numbers.OrderBy(n => n);
var descending = numbers.OrderByDescending(n => n);
var wordsByLength = words.OrderBy(w => w.Length).ThenBy(w => w);

// Grouping
var numbersByRemainder = numbers.GroupBy(n => n % 3);
foreach (var group in numbersByRemainder)
{
    Console.WriteLine($"Remainder {group.Key}: {string.Join(", ", group)}");
}

// Aggregation
int sum = numbers.Sum();
double average = numbers.Average();
int min = numbers.Min();
int max = numbers.Max();
int count = numbers.Count(n => n > 5);
bool any = numbers.Any(n => n > 8);
bool all = numbers.All(n => n > 0);

// Custom aggregation
int product = numbers.Aggregate((acc, n) => acc * n);
string concatenated = words.Aggregate((acc, w) => acc + ", " + w);

// Set operations
List<int> set1 = new List<int> {1, 2, 3, 4, 5};
List<int> set2 = new List<int> {4, 5, 6, 7, 8};

var union = set1.Union(set2);           // {1, 2, 3, 4, 5, 6, 7, 8}
var intersection = set1.Intersect(set2); // {4, 5}
var except = set1.Except(set2);         // {1, 2, 3}
var distinct = set1.Concat(set2).Distinct(); // Remove duplicates

// Element operations
int first = numbers.First();
int firstEven = numbers.First(n => n % 2 == 0);
int firstOrDefault = numbers.FirstOrDefault(n => n > 10); // Returns 0 if not found
int last = numbers.Last();
int single = new List<int> {42}.Single(); // Throws if not exactly one element
int elementAt = numbers.ElementAt(3);
```

**Advanced LINQ Techniques:**
```csharp
// Join operations
List<Customer> customers = new List<Customer>
{
    new Customer { Id = 1, Name = "Alice" },
    new Customer { Id = 2, Name = "Bob" },
    new Customer { Id = 3, Name = "Charlie" }
};

List<Order> orders = new List<Order>
{
    new Order { Id = 101, CustomerId = 1, Amount = 100 },
    new Order { Id = 102, CustomerId = 1, Amount = 200 },
    new Order { Id = 103, CustomerId = 2, Amount = 150 }
};

// Inner join
var customerOrders = from c in customers
                     join o in orders on c.Id equals o.CustomerId
                     select new { c.Name, o.Id, o.Amount };

// Method syntax
var customerOrdersMethod = customers
    .Join(orders, c => c.Id, o => o.CustomerId, 
          (c, o) => new { c.Name, o.Id, o.Amount });

// Group join (left outer join)
var customersWithOrders = from c in customers
                         join o in orders on c.Id equals o.CustomerId into customerOrders
                         select new 
                         { 
                             Customer = c.Name, 
                             Orders = customerOrders.ToList(),
                             OrderCount = customerOrders.Count(),
                             TotalAmount = customerOrders.Sum(x => x.Amount)
                         };

// Method syntax
var customersWithOrdersMethod = customers
    .GroupJoin(orders, c => c.Id, o => o.CustomerId,
               (c, orderGroup) => new 
               { 
                   Customer = c.Name, 
                   Orders = orderGroup.ToList(),
                   OrderCount = orderGroup.Count(),
                   TotalAmount = orderGroup.Sum(x => x.Amount)
               });

// Complex queries with multiple operations
var complexQuery = customers
    .Where(c => c.Name.StartsWith("A"))
    .SelectMany(c => orders.Where(o => o.CustomerId == c.Id), 
                (c, o) => new { Customer = c, Order = o })
    .GroupBy(x => x.Customer.Id)
    .Select(g => new 
    {
        CustomerId = g.Key,
        CustomerName = g.First().Customer.Name,
        TotalOrders = g.Count(),
        TotalAmount = g.Sum(x => x.Order.Amount),
        AverageAmount = g.Average(x => x.Order.Amount)
    })
    .OrderByDescending(x => x.TotalAmount);
```

**LINQ to Objects vs LINQ to SQL/EF:**
```csharp
// LINQ to Objects (in-memory collections)
List<Product> products = GetProductsFromMemory();
var expensiveProducts = products
    .Where(p => p.Price > 100)  // Executed immediately in memory
    .OrderBy(p => p.Name)
    .ToList();

// LINQ to Entities (Entity Framework)
using (var context = new ProductContext())
{
    var expensiveProductsEF = context.Products
        .Where(p => p.Price > 100)  // Translated to SQL
        .OrderBy(p => p.Name)
        .ToList();  // Query executed here
}

// Deferred execution demonstration
var query = numbers.Where(n => 
{
    Console.WriteLine($"Processing {n}");
    return n > 5;
});

Console.WriteLine("Query created");
// Nothing printed yet - query not executed

foreach (var item in query)
{
    Console.WriteLine($"Result: {item}");
}
// Now "Processing X" messages appear

// Force immediate execution
var list = query.ToList();     // Execute now
var array = query.ToArray();   // Execute now
var count = query.Count();     // Execute now
```

### Week 9-10: Delegates, Events, and Lambda Expressions

#### Delegates Deep Dive

**Delegate Basics:**
```csharp
// Delegate declaration
public delegate int MathOperation(int a, int b);
public delegate void LogMessage(string message);
public delegate bool Predicate<T>(T item);

// Methods that match delegate signatures
public static int Add(int a, int b) => a + b;
public static int Multiply(int a, int b) => a * b;
public static void ConsoleLog(string message) => Console.WriteLine($"Log: {message}");
public static void FileLog(string message) => File.AppendAllText("log.txt", $"{DateTime.Now}: {message}\n");

// Using delegates
MathOperation operation = Add;
int result = operation(5, 3); // Calls Add method

// Delegate assignment and combination
LogMessage logger = ConsoleLog;
logger += FileLog; // Multicast delegate
logger("This message goes to both console and file");

// Remove methods from multicast delegate
logger -= ConsoleLog; // Now only logs to file

// Null delegate handling
logger?.Invoke("Safe invocation");

// Generic delegates
Predicate<int> isEven = x => x % 2 == 0;
Predicate<string> isLongWord = s => s.Length > 5;

bool result1 = isEven(4);        // true
bool result2 = isLongWord("hello"); // false
```

**Built-in Delegate Types:**
```csharp
// Action delegates (void return type)
Action simpleAction = () => Console.WriteLine("No parameters");
Action<string> actionWithParam = message => Console.WriteLine(message);
Action<int, string> actionWithTwoParams = (id, name) => Console.WriteLine($"ID: {id}, Name: {name}");

simpleAction();
actionWithParam("Hello World");
actionWithTwoParams(1, "Alice");

// Func delegates (with return type)
Func<int> getRandomNumber = () => new Random().Next(1, 101);
Func<int, int> square = x => x * x;
Func<int, int, int> add = (a, b) => a + b;
Func<string, int, bool> stringHasLength = (str, len) => str.Length == len;

int random = getRandomNumber();
int squared = square(5);
int sum = add(3, 7);
bool hasLength = stringHasLength("hello", 5);

// Predicate delegate (returns bool)
Predicate<int> isPositive = x => x > 0;
Predicate<string> startsWithA = s => s.StartsWith("A", StringComparison.OrdinalIgnoreCase);

List<int> numbers = new List<int> {-2, -1, 0, 1, 2, 3};
List<int> positiveNumbers = numbers.FindAll(isPositive);

// Comparison delegate
Comparison<Person> compareByAge = (p1, p2) => p1.Age.CompareTo(p2.Age);
Comparison<Person> compareByName = (p1, p2) => string.Compare(p1.Name, p2.Name, StringComparison.OrdinalIgnoreCase);

List<Person> people = GetPeople();
people.Sort(compareByAge);
```

**Lambda Expressions:**
```csharp
// Lambda expression syntax variations
Func<int, int> square1 = x => x * x;                    // Expression lambda
Func<int, int> square2 = (x) => x * x;                  // Parentheses optional for single parameter
Func<int, int> square3 = (int x) => x * x;              // Explicit type
Func<int, int, int> add1 = (x, y) => x + y;             // Multiple parameters
Action<string> log1 = message => Console.WriteLine(message); // Action lambda

// Statement lambdas (multiple statements)
Func<int, int> complexOperation = x =>
{
    Console.WriteLine($"Processing {x}");
    int result = x * x + 2 * x + 1;
    Console.WriteLine($"Result: {result}");
    return result;
};

// Capturing variables (closures)
int multiplier = 10;
Func<int, int> multiplyByTen = x => x * multiplier; // Captures 'multiplier'

// Modifying captured variables
int counter = 0;
Action increment = () => counter++; // Captures 'counter' by reference
increment();
increment();
Console.WriteLine(counter); // Output: 2

// Local functions vs lambdas
int CalculateWithLocalFunction(int x)
{
    // Local function
    int Square(int n) => n * n;
    int Double(int n) => n * 2;
    
    return Square(x) + Double(x);
}

Func<int, int> calculateWithLambda = x =>
{
    // Lambda expressions
    Func<int, int> square = n => n * n;
    Func<int, int> double = n => n * 2;
    
    return square(x) + double(x);
};
```

**Advanced Delegate Patterns:**
```csharp
// Delegate composition and chaining
public class EventProcessor
{
    public delegate void ProcessStep(string data);
    
    public static void ValidateData(string data)
    {
        Console.WriteLine($"Validating: {data}");
        if (string.IsNullOrEmpty(data))
            throw new ArgumentException("Data cannot be null or empty");
    }
    
    public static void TransformData(string data)
    {
        Console.WriteLine($"Transforming: {data}");
    }
    
    public static void SaveData(string data)
    {
        Console.WriteLine($"Saving: {data}");
    }
    
    public static void ProcessData(string data, ProcessStep processor)
    {
        try
        {
            processor?.Invoke(data);
            Console.WriteLine("Processing completed successfully");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Processing failed: {ex.Message}");
        }
    }
}

// Usage
ProcessStep pipeline = EventProcessor.ValidateData;
pipeline += EventProcessor.TransformData;
pipeline += EventProcessor.SaveData;

EventProcessor.ProcessData("sample data", pipeline);

// Exception handling in multicast delegates
Action<string> loggers = message => Console.WriteLine($"Console: {message}");
loggers += message => throw new InvalidOperationException("File logger failed");
loggers += message => Console.WriteLine($"Database: {message}");

// Handle exceptions in multicast delegates
foreach (Action<string> logger in loggers.GetInvocationList())
{
    try
    {
        logger("Test message");
    }
    catch (Exception ex)
    {
        Console.WriteLine($"Logger failed: {ex.Message}");
    }
}
```

#### Events

**Event Declaration and Usage:**
```csharp
// Publisher class
public class NewsAgency
{
    // Event declaration using built-in EventHandler
    public event EventHandler<NewsEventArgs> NewsPublished;
    
    // Custom event with custom delegate
    public delegate void BreakingNewsHandler(string headline, DateTime timestamp);
    public event BreakingNewsHandler BreakingNewsAlert;
    
    // Property-like events with custom accessors
    private EventHandler<NewsEventArgs> _specialNewsEvent;
    public event EventHandler<NewsEventArgs> SpecialNews
    {
        add
        {
            Console.WriteLine("Subscriber added to SpecialNews");
            _specialNewsEvent += value;
        }
        remove
        {
            Console.WriteLine("Subscriber removed from SpecialNews");
            _specialNewsEvent -= value;
        }
    }
    
    // Method to raise events
    public void PublishNews(string headline, string content, NewsCategory category)
    {
        var eventArgs = new NewsEventArgs(headline, content, category);
        
        // Raise the event safely
        OnNewsPublished(eventArgs);
        
        // Raise breaking news if urgent
        if (category == NewsCategory.Breaking)
        {
            OnBreakingNews(headline, DateTime.Now);
        }
    }
    
    // Protected virtual method to raise event (allows derived classes to override)
    protected virtual void OnNewsPublished(NewsEventArgs e)
    {
        NewsPublished?.Invoke(this, e);
    }
    
    protected virtual void OnBreakingNews(string headline, DateTime timestamp)
    {
        BreakingNewsAlert?.Invoke(headline, timestamp);
    }
    
    protected virtual void OnSpecialNews(NewsEventArgs e)
    {
        _specialNewsEvent?.Invoke(this, e);
    }
}

// Event arguments class
public class NewsEventArgs : EventArgs
{
    public string Headline { get; }
    public string Content { get; }
    public NewsCategory Category { get; }
    public DateTime Timestamp { get; }
    
    public NewsEventArgs(string headline, string content, NewsCategory category)
    {
        Headline = headline;
        Content = content;
        Category = category;
        Timestamp = DateTime.Now;
    }
}

public enum NewsCategory
{
    General,
    Sports,
    Technology,
    Breaking
}

// Subscriber classes
public class NewsSubscriber
{
    public string Name { get; }
    
    public NewsSubscriber(string name)
    {
        Name = name;
    }
    
    public void Subscribe(NewsAgency agency)
    {
        // Subscribe to events
        agency.NewsPublished += OnNewsReceived;
        agency.BreakingNewsAlert += OnBreakingNewsReceived;
    }
    
    public void Unsubscribe(NewsAgency agency)
    {
        // Unsubscribe from events
        agency.NewsPublished -= OnNewsReceived;
        agency.BreakingNewsAlert -= OnBreakingNewsReceived;
    }
    
    private void OnNewsReceived(object sender, NewsEventArgs e)
    {
        Console.WriteLine($"{Name} received news: {e.Headline} [{e.Category}]");
    }
    
    private void OnBreakingNewsReceived(string headline, DateTime timestamp)
    {
        Console.WriteLine($"{Name} BREAKING NEWS ALERT: {headline} at {timestamp:HH:mm:ss}");
    }
}

// Usage
NewsAgency agency = new NewsAgency();
NewsSubscriber subscriber1 = new NewsSubscriber("Alice");
NewsSubscriber subscriber2 = new NewsSubscriber("Bob");

subscriber1.Subscribe(agency);
subscriber2.Subscribe(agency);

agency.PublishNews("Tech Conference Announced", "Annual tech conference...", NewsCategory.Technology);
agency.PublishNews("Market Crash!", "Stock market...", NewsCategory.Breaking);

subscriber1.Unsubscribe(agency);
```

**Advanced Event Patterns:**
```csharp
// Weak event pattern (prevents memory leaks)
public class WeakEventManager
{
    private readonly List<WeakReference> _subscribers = new List<WeakReference>();
    
    public void Subscribe(EventHandler handler)
    {
        _subscribers.Add(new WeakReference(handler));
    }
    
    public void Unsubscribe(EventHandler handler)
    {
        _subscribers.RemoveAll(wr => !wr.IsAlive || ReferenceEquals(wr.Target, handler));
    }
    
    public void RaiseEvent(object sender, EventArgs e)
    {
        var deadReferences = new List<WeakReference>();
        
        foreach (var weakRef in _subscribers)
        {
            if (weakRef.IsAlive)
            {
                if (weakRef.Target is EventHandler handler)
                {
                    handler(sender, e);
                }
            }
            else
            {
                deadReferences.Add(weakRef);
            }
        }
        
        // Clean up dead references
        foreach (var deadRef in deadReferences)
        {
            _subscribers.Remove(deadRef);
        }
    }
}

// Event aggregator pattern
public class EventAggregator
{
    private readonly Dictionary<Type, List<object>> _subscribers = new Dictionary<Type, List<object>>();
    
    public void Subscribe<T>(Action<T> handler)
    {
        if (!_subscribers.ContainsKey(typeof(T)))
        {
            _subscribers[typeof(T)] = new List<object>();
        }
        _subscribers[typeof(T)].Add(handler);
    }
    
    public void Unsubscribe<T>(Action<T> handler)
    {
        if (_subscribers.ContainsKey(typeof(T)))
        {
            _subscribers[typeof(T)].Remove(handler);
        }
    }
    
    public void Publish<T>(T eventData)
    {
        if (_subscribers.ContainsKey(typeof(T)))
        {
            foreach (var subscriber in _subscribers[typeof(T)].Cast<Action<T>>())
            {
                subscriber(eventData);
            }
        }
    }
}

// Usage
EventAggregator eventAggregator = new EventAggregator();

// Subscribe to different event types
eventAggregator.Subscribe<string>(message => Console.WriteLine($"String event: {message}"));
eventAggregator.Subscribe<int>(number => Console.WriteLine($"Int event: {number}"));

// Publish events
eventAggregator.Publish("Hello World");
eventAggregator.Publish(42);
```

## Phase 3: Advanced

### Week 11-12: Asynchronous Programming

#### Understanding Async/Await

**Basic Async/Await Concepts:**
```csharp
// Synchronous method (blocking)
public static void DownloadDataSync()
{
    using (var client = new HttpClient())
    {
        string data = client.GetStringAsync("https://api.example.com/data").Result; // Blocks thread
        Console.WriteLine($"Downloaded {data.Length} characters");
    }
}

// Asynchronous method (non-blocking)
public static async Task DownloadDataAsync()
{
    using (var client = new HttpClient())
    {
        string data = await client.GetStringAsync("https://api.example.com/data"); // Doesn't block
        Console.WriteLine($"Downloaded {data.Length} characters");
    }
}

// Async method with return value
public static async Task<string> GetDataAsync()
{
    using (var client = new HttpClient())
    {
        return await client.GetStringAsync("https://api.example.com/data");
    }
}

// Multiple async operations
public static async Task ProcessMultipleUrlsAsync()
{
    string[] urls = 
    {
        "https://api.example.com/data1",
        "https://api.example.com/data2",
        "https://api.example.com/data3"
    };
    
    using (var client = new HttpClient())
    {
        // Sequential processing (slower)
        foreach (string url in urls)
        {
            string data = await client.GetStringAsync(url);
            Console.WriteLine($"Downloaded from {url}: {data.Length} characters");
        }
        
        // Parallel processing (faster)
        Task<string>[] tasks = urls.Select(url => client.GetStringAsync(url)).ToArray();
        string[] results = await Task.WhenAll(tasks);
        
        for (int i = 0; i < urls.Length; i++)
        {
            Console.WriteLine($"Downloaded from {urls[i]}: {results[i].Length} characters");
        }
    }
}
```

**Task and Task<T> in Detail:**
```csharp
// Creating tasks
Task task1 = Task.Run(() => DoWork());
Task<int> task2 = Task.Run(() => CalculateResult());
Task<string> task3 = Task.FromResult("Immediate result"); // Completed task

// Task factory
Task task4 = Task.Factory.StartNew(() => DoWork(), TaskCreationOptions.LongRunning);

// Task with cancellation
CancellationTokenSource cts = new CancellationTokenSource();
Task task5 = Task.Run(() => DoWorkWithCancellation(cts.Token), cts.Token);

// Task continuation
Task.Run(() => DoWork())
    .ContinueWith(t => 
    {
        if (t.IsCompletedSuccessfully)
        {
            Console.WriteLine("Work completed successfully");
        }
        else if (t.IsFaulted)
        {
            Console.WriteLine($"Work failed: {t.Exception?.GetBaseException().Message}");
        }
    });

// Task status and properties
Task longRunningTask = Task.Run(() => Thread.Sleep(5000));
Console.WriteLine($"Status: {longRunningTask.Status}");
Console.WriteLine($"Is completed: {longRunningTask.IsCompleted}");
Console.WriteLine($"Is running: {longRunningTask.Status == TaskStatus.Running}");

// Waiting for tasks
Task.WaitAll(task1, task2); // Wait for all to complete
Task.WaitAny(task1, task2); // Wait for any to complete

// Timeout and cancellation
bool completed = Task.WaitAll(new[] { task1, task2 }, TimeSpan.FromSeconds(10));
if (!completed)
{
    Console.WriteLine("Tasks did not complete within timeout");
}
```

**Advanced Async Patterns:**
```csharp
// Async enumerable (C# 8+)
public static async IAsyncEnumerable<int> GenerateNumbersAsync()
{
    for (int i = 0; i < 10; i++)
    {
        await Task.Delay(1000); // Simulate async work
        yield return i;
    }
}

// Consuming async enumerable
await foreach (int number in GenerateNumbersAsync())
{
    Console.WriteLine($"Received: {number}");
}

// Async using (C# 8+)
public class AsyncDisposableResource : IAsyncDisposable
{
    public async ValueTask DisposeAsync()
    {
        await Task.Delay(100); // Simulate cleanup
        Console.WriteLine("Resource disposed asynchronously");
    }
}

await using (var resource = new AsyncDisposableResource())
{
    // Use resource
}

// ConfigureAwait usage
public async Task<string> GetDataAsync()
{
    // In library code, use ConfigureAwait(false) to avoid deadlocks
    string data = await httpClient.GetStringAsync(url).ConfigureAwait(false);
    return ProcessData(data);
}

// Async lazy initialization
private readonly AsyncLazy<ExpensiveResource> _expensiveResource = 
    new AsyncLazy<ExpensiveResource>(() => InitializeResourceAsync());

public async Task<string> UseResourceAsync()
{
    var resource = await _expensiveResource.GetAwaiter();
    return resource.GetData();
}
```

**Error Handling in Async Code:**
```csharp
// Basic try-catch with async
public async Task<string> DownloadWithErrorHandlingAsync(string url)
{
    try
    {
        using (var client = new HttpClient())
        {
            return await client.GetStringAsync(url);
        }
    }
    catch (HttpRequestException ex)
    {
        Console.WriteLine($"HTTP error: {ex.Message}");
        throw; // Re-throw to propagate
    }
    catch (TaskCanceledException ex)
    {
        Console.WriteLine($"Request timed out: {ex.Message}");
        return "Default content due to timeout";
    }
    catch (Exception ex)
    {
        Console.WriteLine($"Unexpected error: {ex.Message}");
        throw new ApplicationException("Failed to download data", ex);
    }
}

// Handling multiple async operations
public async Task ProcessMultipleOperationsAsync()
{
    var tasks = new[]
    {
        DownloadWithErrorHandlingAsync("https://api1.example.com"),
        DownloadWithErrorHandlingAsync("https://api2.example.com"),
        DownloadWithErrorHandlingAsync("https://api3.example.com")
    };
    
    try
    {
        string[] results = await Task.WhenAll(tasks);
        // All succeeded
        ProcessResults(results);
    }
    catch (Exception ex)
    {
        // At least one failed
        Console.WriteLine($"One or more operations failed: {ex.Message}");
        
        // Check individual task results
        for (int i = 0; i < tasks.Length; i++)
        {
            if (tasks[i].IsCompletedSuccessfully)
            {
                Console.WriteLine($"Task {i} succeeded: {tasks[i].Result.Length} characters");
            }
            else if (tasks[i].IsFaulted)
            {
                Console.WriteLine($"Task {i} failed: {tasks[i].Exception?.GetBaseException().Message}");
            }
        }
    }
}
```

**Cancellation with CancellationToken:**
```csharp
// Method that supports cancellation
public async Task<string> DownloadDataAsync(string url, CancellationToken cancellationToken = default)
{
    using (var client = new HttpClient())
    {
        try
        {
            // Pass cancellation token to async operations
            return await client.GetStringAsync(url, cancellationToken);
        }
        catch (OperationCanceledException)
        {
            Console.WriteLine("Download was cancelled");
            throw; // Re-throw cancellation
        }
    }
}

// Long-running operation with periodic cancellation checks
public async Task ProcessLargeDatasetAsync(IEnumerable<string> items, CancellationToken cancellationToken = default)
{
    foreach (string item in items)
    {
        // Check for cancellation periodically
        cancellationToken.ThrowIfCancellationRequested();
        
        // Simulate work
        await ProcessItemAsync(item);
        
        // Alternative: check and handle gracefully
        if (cancellationToken.IsCancellationRequested)
        {
            Console.WriteLine("Processing cancelled gracefully");
            return;
        }
    }
}

// Using cancellation
public async Task DemonstrateCancellationAsync()
{
    using (var cts = new CancellationTokenSource())
    {
        // Cancel after 5 seconds
        cts.CancelAfter(TimeSpan.FromSeconds(5));
        
        try
        {
            string result = await DownloadDataAsync("https://slow-api.example.com", cts.Token);
            Console.WriteLine($"Downloaded: {result.Length} characters");
        }
        catch (OperationCanceledException)
        {
            Console.WriteLine("Operation was cancelled");
        }
    }
    
    // Manual cancellation
    using (var cts = new CancellationTokenSource())
    {
        // Start long-running operation
        Task processTask = ProcessLargeDatasetAsync(GetLargeDataset(), cts.Token);
        
        // Cancel after user input
        Console.WriteLine("Press any key to cancel...");
        Console.ReadKey();
        cts.Cancel();
        
        await processTask;
    }
}

// Combining cancellation tokens
public async Task OperationWithMultipleCancellationSourcesAsync()
{
    using (var timeoutCts = new CancellationTokenSource(TimeSpan.FromMinutes(5)))
    using (var userCts = new CancellationTokenSource())
    using (var combinedCts = CancellationTokenSource.CreateLinkedTokenSource(timeoutCts.Token, userCts.Token))
    {
        try
        {
            await LongRunningOperationAsync(combinedCts.Token);
        }
        catch (OperationCanceledException)
        {
            if (timeoutCts.Token.IsCancellationRequested)
            {
                Console.WriteLine("Operation timed out");
            }
            else if (userCts.Token.IsCancellationRequested)
            {
                Console.WriteLine("Operation cancelled by user");
            }
        }
    }
}
```

### Week 13-14: Multithreading and Parallel Programming

#### Thread Fundamentals

**Basic Threading:**
```csharp
// Creating and starting threads
Thread thread1 = new Thread(() => 
{
    for (int i = 0; i < 5; i++)
    {
        Console.WriteLine($"Thread 1: {i}");
        Thread.Sleep(1000);
    }
});

Thread thread2 = new Thread(WorkerMethod);

// Thread properties
thread1.Name = "Worker Thread 1";
thread1.IsBackground = true; // Dies when main thread dies
thread1.Priority = ThreadPriority.Normal;

thread1.Start();
thread2.Start();

// Wait for threads to complete
thread1.Join();
thread2.Join(5000); // Wait maximum 5 seconds

static void WorkerMethod()
{
    Console.WriteLine($"Current thread: {Thread.CurrentThread.Name}");
    Console.WriteLine($"Thread ID: {Thread.CurrentThread.ManagedThreadId}");
    Console.WriteLine($"Is background: {Thread.CurrentThread.IsBackground}");
}

// Parameterized threads
Thread paramThread = new Thread((object param) => 
{
    string message = (string)param;
    Console.WriteLine($"Received parameter: {message}");
});
paramThread.Start("Hello from parameter");

// Thread-safe operations
private static int _counter = 0;
private static readonly object _lockObject = new object();

public static void IncrementCounter()
{
    for (int i = 0; i < 1000; i++)
    {
        lock (_lockObject)
        {
            _counter++; // Thread-safe increment
        }
    }
}

// Demonstrating race conditions and fixes
public static void DemonstrateThreadSafety()
{
    // Without synchronization (race condition)
    _counter = 0;
    Thread[] threads = new Thread[10];
    
    for (int i = 0; i < 10; i++)
    {
        threads[i] = new Thread(() => 
        {
            for (int j = 0; j < 1000; j++)
            {
                _counter++; // Not thread-safe!
            }
        });
        threads[i].Start();
    }
    
    foreach (Thread thread in threads)
        thread.Join();
    
    Console.WriteLine($"Expected: 10000, Actual: {_counter}"); // Likely less than 10000
    
    // With synchronization
    _counter = 0;
    for (int i = 0; i < 10; i++)
    {
        threads[i] = new Thread(IncrementCounter);
        threads[i].Start();
    }
    
    foreach (Thread thread in threads)
        thread.Join();
    
    Console.WriteLine($"Expected: 10000, Actual: {_counter}"); // Should be 10000
}
```

**Synchronization Primitives:**
```csharp
// Lock statement (Monitor wrapper)
private static readonly object _lockObj = new object();
private static int _sharedResource = 0;

public static void SafeIncrement()
{
    lock (_lockObj)
    {
        _sharedResource++;
        Console.WriteLine($"Thread {Thread.CurrentThread.ManagedThreadId}: {_sharedResource}");
    }
}

// Monitor class (lower-level than lock)
public static void MonitorExample()
{
    bool lockTaken = false;
    try
    {
        Monitor.Enter(_lockObj, ref lockTaken);
        _sharedResource++;
        
        // Wait for condition
        if (_sharedResource < 10)
        {
            Monitor.Wait(_lockObj); // Releases lock and waits
        }
        
        // Signal other threads
        Monitor.PulseAll(_lockObj); // Wake up all waiting threads
    }
    finally
    {
        if (lockTaken)
            Monitor.Exit(_lockObj);
    }
}

// Mutex (inter-process synchronization)
using (Mutex mutex = new Mutex(false, "Global\\MyApplicationMutex"))
{
    if (mutex.WaitOne(TimeSpan.FromSeconds(5)))
    {
        try
        {
            // Critical section - only one process can execute this
            Console.WriteLine("Acquired mutex");
            Thread.Sleep(2000);
        }
        finally
        {
            mutex.ReleaseMutex();
        }
    }
    else
    {
        Console.WriteLine("Failed to acquire mutex within timeout");
    }
}

// Semaphore (limit concurrent access)
Semaphore semaphore = new Semaphore(2, 2); // Allow 2 concurrent threads

void AccessResource()
{
    semaphore.WaitOne(); // Acquire permit
    try
    {
        Console.WriteLine($"Thread {Thread.CurrentThread.ManagedThreadId} accessing resource");
        Thread.Sleep(2000); // Simulate work
    }
    finally
    {
        semaphore.Release(); // Return permit
    }
}

// AutoResetEvent (signal single thread)
AutoResetEvent autoEvent = new AutoResetEvent(false);

Thread producer = new Thread(() =>
{
    for (int i = 0; i < 5; i++)
    {
        Console.WriteLine($"Producing item {i}");
        Thread.Sleep(1000);
        autoEvent.Set(); // Signal one waiting thread
    }
});

Thread consumer = new Thread(() =>
{
    for (int i = 0; i < 5; i++)
    {
        autoEvent.WaitOne(); // Wait for signal
        Console.WriteLine($"Consumed item {i}");
    }
});

// ManualResetEvent (signal all threads)
ManualResetEvent manualEvent = new ManualResetEvent(false);

Thread waiter1 = new Thread(() =>
{
    Console.WriteLine("Waiter 1 waiting...");
    manualEvent.WaitOne();
    Console.WriteLine("Waiter 1 signaled!");
});

Thread waiter2 = new Thread(() =>
{
    Console.WriteLine("Waiter 2 waiting...");
    manualEvent.WaitOne();
    Console.WriteLine("Waiter 2 signaled!");
});

waiter1.Start();
waiter2.Start();

Thread.Sleep(2000);
manualEvent.Set(); // Signal all waiting threads

// CountdownEvent (wait for multiple operations)
CountdownEvent countdown = new CountdownEvent(3);

for (int i = 0; i < 3; i++)
{
    int taskId = i;
    new Thread(() =>
    {
        Console.WriteLine($"Task {taskId} starting");
        Thread.Sleep(1000 * (taskId + 1));
        Console.WriteLine($"Task {taskId} completed");
        countdown.Signal(); // Decrement count
    }).Start();
}

countdown.Wait(); // Wait for all tasks to complete
Console.WriteLine("All tasks completed!");
```

**Thread-Safe Collections:**
```csharp
// ConcurrentQueue<T>
ConcurrentQueue<string> queue = new ConcurrentQueue<string>();

// Producer threads
for (int i = 0; i < 3; i++)
{
    int producerId = i;
    new Thread(() =>
    {
        for (int j = 0; j < 10; j++)
        {
            string item = $"Producer{producerId}-Item{j}";
            queue.Enqueue(item);
            Console.WriteLine($"Enqueued: {item}");
            Thread.Sleep(100);
        }
    }).Start();
}

// Consumer threads
for (int i = 0; i < 2; i++)
{
    int consumerId = i;
    new Thread(() =>
    {
        while (true)
        {
            if (queue.TryDequeue(out string item))
            {
                Console.WriteLine($"Consumer{consumerId} dequeued: {item}");
                Thread.Sleep(150);
            }
            else
            {
                Thread.Sleep(50); // No items available
            }
        }
    }).Start();
}

// ConcurrentDictionary<TKey, TValue>
ConcurrentDictionary<int, string> concurrentDict = new ConcurrentDictionary<int, string>();

// Thread-safe operations
concurrentDict.TryAdd(1, "One");
concurrentDict.TryUpdate(1, "Updated One", "One");
concurrentDict.AddOrUpdate(2, "Two", (key, oldValue) => "Updated Two");
string value = concurrentDict.GetOrAdd(3, key => $"Generated value for {key}");

// ConcurrentBag<T> (unordered collection)
ConcurrentBag<int> bag = new ConcurrentBag<int>();

Parallel.For(0, 1000, i =>
{
    bag.Add(i);
});

// BlockingCollection<T> (producer-consumer pattern)
using (BlockingCollection<int> collection = new BlockingCollection<int>())
{
    // Producer
    Task producer = Task.Run(() =>
    {
        for (int i = 0; i < 100; i++)
        {
            collection.Add(i);
            Thread.Sleep(10);
        }
        collection.CompleteAdding(); // Signal no more items
    });
    
    // Consumer
    Task consumer = Task.Run(() =>
    {
        foreach (int item in collection.GetConsumingEnumerable())
        {
            Console.WriteLine($"Processing: {item}");
            Thread.Sleep(20);
        }
    });
    
    Task.WaitAll(producer, consumer);
}
```

#### Parallel Programming with PLINQ and Parallel Class

**Parallel.For and Parallel.ForEach:**
```csharp
// Sequential vs Parallel processing
int[] largeArray = Enumerable.Range(0, 10_000_000).ToArray();

// Sequential processing
Stopwatch sw = Stopwatch.StartNew();
for (int i = 0; i < largeArray.Length; i++)
{
    largeArray[i] = ExpensiveComputation(largeArray[i]);
}
sw.Stop();
Console.WriteLine($"Sequential: {sw.ElapsedMilliseconds}ms");

// Parallel processing
sw.Restart();
Parallel.For(0, largeArray.Length, i =>
{
    largeArray[i] = ExpensiveComputation(largeArray[i]);
});
sw.Stop();
Console.WriteLine($"Parallel: {sw.ElapsedMilliseconds}ms");

// Parallel.ForEach
List<string> urls = GetUrls();
ConcurrentBag<string> results = new ConcurrentBag<string>();

Parallel.ForEach(urls, url =>
{
    string content = DownloadContent(url);
    results.Add(content);
});

// Parallel options and cancellation
ParallelOptions options = new ParallelOptions
{
    MaxDegreeOfParallelism = Environment.ProcessorCount / 2,
    CancellationToken = cancellationToken
};

try
{
    Parallel.For(0, 1000, options, (i, loopState) =>
    {
        if (options.CancellationToken.IsCancellationRequested)
        {
            loopState.Stop();
            return;
        }
        
        // Break vs Stop
        if (SomeCondition(i))
        {
            loopState.Break(); // Complete all iterations with index < current
            // or
            // loopState.Stop(); // Stop as soon as possible
        }
        
        ProcessItem(i);
    });
}
catch (OperationCanceledException)
{
    Console.WriteLine("Parallel operation was cancelled");
}

// Partitioning for better load balancing
Partitioner<int> partitioner = Partitioner.Create(0, largeArray.Length, true);
Parallel.ForEach(partitioner, partition =>
{
    for (int i = partition.Item1; i < partition.Item2; i++)
    {
        ProcessItem(largeArray[i]);
    }
});

static int ExpensiveComputation(int input)
{
    // Simulate CPU-intensive work
    Thread.Sleep(1);
    return input * input;
}
```

**PLINQ (Parallel LINQ):**
```csharp
// Basic PLINQ queries
int[] numbers = Enumerable.Range(1, 1_000_000).ToArray();

// Sequential LINQ
var sequentialResult = numbers
    .Where(n => IsPrime(n))
    .Select(n => n * n)
    .ToArray();

// Parallel LINQ
var parallelResult = numbers
    .AsParallel()
    .Where(n => IsPrime(n))
    .Select(n => n * n)
    .ToArray();

// PLINQ with ordering
var orderedParallelResult = numbers
    .AsParallel()
    .AsOrdered() // Maintain original order
    .Where(n => n % 2 == 0)
    .Select(n => n * 2)
    .Take(1000)
    .ToArray();

// Degree of parallelism
var limitedParallelResult = numbers
    .AsParallel()
    .WithDegreeOfParallelism(2) // Use only 2 cores
    .Where(n => IsPrime(n))
    .ToArray();

// Execution mode
var forcedParallelResult = numbers
    .AsParallel()
    .WithExecutionMode(ParallelExecutionMode.ForceParallelism)
    .Where(n => n > 100) // Force parallel even for simple operations
    .ToArray();

// Exception handling in PLINQ
try
{
    var resultWithExceptions = numbers
        .AsParallel()
        .Select(n => 
        {
            if (n % 1000 == 0)
                throw new InvalidOperationException($"Error processing {n}");
            return n * 2;
        })
        .ToArray();
}
catch (AggregateException ae)
{
    foreach (Exception ex in ae.InnerExceptions)
    {
        Console.WriteLine($"Exception: {ex.Message}");
    }
}

// Custom partitioning in PLINQ
var customPartitioned = Partitioner
    .Create(numbers, true) // Load balancing enabled
    .AsParallel()
    .Where(n => IsPrime(n))
    .ToArray();

// PLINQ aggregation
int sum = numbers.AsParallel().Sum();
double average = numbers.AsParallel().Average();
int max = numbers.AsParallel().Max();

// Custom aggregation
int parallelSum = numbers
    .AsParallel()
    .Aggregate(
        seed: 0,
        func: (acc, n) => acc + n,
        resultSelector: result => result
    );

// Parallel aggregation with intermediate results
var parallelSumAdvanced = numbers
    .AsParallel()
    .Aggregate(
        seed: 0,
        func: (localSum, n) => localSum + n,
        localFinally: localSum => localSum,
        resultSelector: results => results.Sum()
    );

static bool IsPrime(int number)
{
    if (number < 2) return false;
    for (int i = 2; i <= Math.Sqrt(number); i++)
    {
        if (number % i == 0) return false;
    }
    return true;
}
```

**Task Parallel Library (TPL):**
```csharp
// Task.Run for CPU-bound work
Task<int> computeTask = Task.Run(() =>
{
    int result = 0;
    for (int i = 0; i < 1_000_000; i++)
    {
        result += i;
    }
    return result;
});

// Task continuation
Task<string> processTask = computeTask.ContinueWith(task =>
{
    if (task.IsCompletedSuccessfully)
    {
        return $"Computation result: {task.Result}";
    }
    return "Computation failed";
}, TaskContinuationOptions.ExecuteSynchronously);

// Task factory with custom scheduler
TaskScheduler scheduler = new LimitedConcurrencyLevelTaskScheduler(2);
Task customSchedulerTask = Task.Factory.StartNew(() =>
{
    Console.WriteLine($"Running on custom scheduler, Thread: {Thread.CurrentThread.ManagedThreadId}");
}, CancellationToken.None, TaskCreationOptions.None, scheduler);

// Parallel Invoke
Parallel.Invoke(
    () => DoWork("Task 1"),
    () => DoWork("Task 2"),
    () => DoWork("Task 3")
);

// Task coordination
Task[] tasks = new Task[10];
for (int i = 0; i < 10; i++)
{
    int taskId = i;
    tasks[i] = Task.Run(() => DoWork($"Task {taskId}"));
}

Task.WhenAll(tasks).ContinueWith(t =>
{
    Console.WriteLine("All tasks completed");
});

Task.WhenAny(tasks).ContinueWith(t =>
{
    Console.WriteLine("First task completed");
});

static void DoWork(string taskName)
{
    Console.WriteLine($"{taskName} starting on thread {Thread.CurrentThread.ManagedThreadId}");
    Thread.Sleep(1000);
    Console.WriteLine($"{taskName} completed");
}

// Custom TaskScheduler example
public class LimitedConcurrencyLevelTaskScheduler : TaskScheduler
{
    private readonly LinkedList<Task> _tasks = new LinkedList<Task>();
    private readonly int _maxDegreeOfParallelism;
    private int _delegatesQueuedOrRunning = 0;

    public LimitedConcurrencyLevelTaskScheduler(int maxDegreeOfParallelism)
    {
        if (maxDegreeOfParallelism < 1) throw new ArgumentOutOfRangeException(nameof(maxDegreeOfParallelism));
        _maxDegreeOfParallelism = maxDegreeOfParallelism;
    }

    protected sealed override void QueueTask(Task task)
    {
        lock (_tasks)
        {
            _tasks.AddLast(task);
            if (_delegatesQueuedOrRunning < _maxDegreeOfParallelism)
            {
                ++_delegatesQueuedOrRunning;
                NotifyThreadPoolOfPendingWork();
            }
        }
    }

    private void NotifyThreadPoolOfPendingWork()
    {
        ThreadPool.UnsafeQueueUserWorkItem(_ =>
        {
            try
            {
                while (true)
                {
                    Task item;
                    lock (_tasks)
                    {
                        if (_tasks.Count == 0)
                        {
                            --_delegatesQueuedOrRunning;
                            break;
                        }

                        item = _tasks.First.Value;
                        _tasks.RemoveFirst();
                    }

                    TryExecuteTask(item);
                }
            }
            finally
            {
                lock (_tasks)
                {
                    --_delegatesQueuedOrRunning;
                    if (_tasks.Count > 0)
                    {
                        ++_delegatesQueuedOrRunning;
                        NotifyThreadPoolOfPendingWork();
                    }
                }
            }
        }, null);
    }

    protected sealed override bool TryExecuteTaskInline(Task task, bool taskWasPreviouslyQueued)
    {
        if (!taskWasPreviouslyQueued) return TryExecuteTask(task);
        
        if (TryDequeue(task)) return TryExecuteTask(task);
        else return false;
    }

    protected sealed override bool TryDequeue(Task task)
    {
        lock (_tasks) return _tasks.Remove(task);
    }

    public sealed override int MaximumConcurrencyLevel { get { return _maxDegreeOfParallelism; } }

    protected sealed override IEnumerable<Task> GetScheduledTasks()
    {
        bool lockTaken = false;
        try
        {
            Monitor.TryEnter(_tasks, ref lockTaken);
            if (lockTaken) return _tasks;
            else throw new NotSupportedException();
        }
        finally
        {
            if (lockTaken) Monitor.Exit(_tasks);
        }
    }
}
```

### Week 15-16: Reflection and Attributes

#### Reflection Deep Dive

**Basic Reflection Operations:**
```csharp
// Getting Type information
Type stringType = typeof(string);
Type intType = typeof(int);
Type listType = typeof(List<>); // Generic type definition
Type genericListType = typeof(List<string>); // Generic type

// Getting Type from objects
string text = "Hello";
Type textType = text.GetType();

// Getting Type by name
Type typeByName = Type.GetType("System.String");
Type typeByFullName = Type.GetType("System.Collections.Generic.List`1[System.String]");

// Assembly and type loading
Assembly assembly = Assembly.GetExecutingAssembly();
Type[] types = assembly.GetTypes();

Assembly systemAssembly = Assembly.GetAssembly(typeof(string));
Type stringTypeFromAssembly = systemAssembly.GetType("System.String");

// Type information
Console.WriteLine($"Name: {stringType.Name}");                    // String
Console.WriteLine($"FullName: {stringType.FullName}");            // System.String
Console.WriteLine($"Namespace: {stringType.Namespace}");          // System
Console.WriteLine($"Assembly: {stringType.Assembly.FullName}");
Console.WriteLine($"IsClass: {stringType.IsClass}");              // True
Console.WriteLine($"IsValueType: {stringType.IsValueType}");      // False
Console.WriteLine($"IsGeneric: {genericListType.IsGenericType}"); // True
Console.WriteLine($"IsAbstract: {stringType.IsAbstract}");        // False
Console.WriteLine($"IsSealed: {stringType.IsSealed}");            // True

// Generic type information
if (genericListType.IsGenericType)
{
    Type[] genericArgs = genericListType.GetGenericArguments();
    Type genericTypeDef = genericListType.GetGenericTypeDefinition();
    Console.WriteLine($"Generic arguments: {string.Join(", ", genericArgs.Select(t => t.Name))}");
    Console.WriteLine($"Generic type definition: {genericTypeDef.Name}");
}

// Inheritance hierarchy
Type currentType = typeof(ArgumentException);
while (currentType != null)
{
    Console.WriteLine($"Type: {currentType.Name}");
    currentType = currentType.BaseType;
}
// Output: ArgumentException -> SystemException -> Exception -> Object

// Interface information
Type[] interfaces = typeof(List<string>).GetInterfaces();
foreach (Type iface in interfaces)
{
    Console.WriteLine($"Implements: {iface.Name}");
}
```

**Working with Members:**
```csharp
public class SampleClass
{
    public string PublicField = "Public field value";
    private int _privateField = 42;
    
    public string PublicProperty { get; set; } = "Public property value";
    private string PrivateProperty { get; set; } = "Private property value";
    
    public SampleClass() { }
    public SampleClass(string value) { PublicProperty = value; }
    
    public void PublicMethod() => Console.WriteLine("Public method called");
    private void PrivateMethod() => Console.WriteLine("Private method called");
    
    public static void StaticMethod() => Console.WriteLine("Static method called");
    
    public void MethodWithParameters(int x, string y) => Console.WriteLine($"Parameters: {x}, {y}");
    
    public T GenericMethod<T>(T input) => input;
}

// Getting member information
Type sampleType = typeof(SampleClass);

// Fields
FieldInfo[] fields = sampleType.GetFields(BindingFlags.Public | BindingFlags.NonPublic | BindingFlags.Instance);
foreach (FieldInfo field in fields)
{
    Console.WriteLine($"Field: {field.Name}, Type: {field.FieldType.Name}, IsPublic: {field.IsPublic}");
}

// Properties
PropertyInfo[] properties = sampleType.GetProperties(BindingFlags.Public | BindingFlags.NonPublic | BindingFlags.Instance);
foreach (PropertyInfo property in properties)
{
    Console.WriteLine($"Property: {property.Name}, Type: {property.PropertyType.Name}, CanRead: {property.CanRead}, CanWrite: {property.CanWrite}");
}

// Methods
MethodInfo[] methods = sampleType.GetMethods(BindingFlags.Public | BindingFlags.NonPublic | BindingFlags.Instance | BindingFlags.Static);
foreach (MethodInfo method in methods.Where(m => m.DeclaringType == sampleType)) // Exclude inherited methods
{
    Console.WriteLine($"Method: {method.Name}, IsPublic: {method.IsPublic}, IsStatic: {method.IsStatic}");
    
    // Parameter information
    ParameterInfo[] parameters = method.GetParameters();
    if (parameters.Length > 0)
    {
        Console.WriteLine($"  Parameters: {string.Join(", ", parameters.Select(p => $"{p.ParameterType.Name} {p.Name}"))}");
    }
}

// Constructors
ConstructorInfo[] constructors = sampleType.GetConstructors();
foreach (ConstructorInfo constructor in constructors)
{
    ParameterInfo[] parameters = constructor.GetParameters();
    Console.WriteLine($"Constructor: ({string.Join(", ", parameters.Select(p => $"{p.ParameterType.Name} {p.Name}"))})");
}
```

**Dynamic Member Access:**
```csharp
// Creating instances
Type sampleType = typeof(SampleClass);

// Using Activator
object instance1 = Activator.CreateInstance(sampleType);
object instance2 = Activator.CreateInstance(sampleType, "Constructor parameter");

// Using constructor info
ConstructorInfo constructor = sampleType.GetConstructor(new[] { typeof(string) });
object instance3 = constructor.Invoke(new object[] { "Constructor via reflection" });

// Generic instance creation
Type genericListType = typeof(List<>).MakeGenericType(typeof(int));
object genericList = Activator.CreateInstance(genericListType);

// Field access
SampleClass sample = new SampleClass();
FieldInfo publicField = sampleType.GetField("PublicField");
FieldInfo privateField = sampleType.GetField("_privateField", BindingFlags.NonPublic | BindingFlags.Instance);

// Get field values
string publicFieldValue = (string)publicField.GetValue(sample);
int privateFieldValue = (int)privateField.GetValue(sample);

Console.WriteLine($"Public field: {publicFieldValue}");
Console.WriteLine($"Private field: {privateFieldValue}");

// Set field values
publicField.SetValue(sample, "Modified public field");
privateField.SetValue(sample, 100);

// Property access
PropertyInfo publicProperty = sampleType.GetProperty("PublicProperty");
PropertyInfo privateProperty = sampleType.GetProperty("PrivateProperty", BindingFlags.NonPublic | BindingFlags.Instance);

// Get property values
string publicPropertyValue = (string)publicProperty.GetValue(sample);
string privatePropertyValue = (string)privateProperty.GetValue(sample);

// Set property values
publicProperty.SetValue(sample, "Modified public property");
privateProperty.SetValue(sample, "Modified private property");

// Method invocation
MethodInfo publicMethod = sampleType.GetMethod("PublicMethod");
MethodInfo privateMethod = sampleType.GetMethod("PrivateMethod", BindingFlags.NonPublic | BindingFlags.Instance);
MethodInfo methodWithParams = sampleType.GetMethod("MethodWithParameters");
MethodInfo staticMethod = sampleType.GetMethod("StaticMethod");

// Invoke methods
publicMethod.Invoke(sample, null);
privateMethod.Invoke(sample, null);
methodWithParams.Invoke(sample, new object[] { 42, "Hello" });
staticMethod.Invoke(null, null); // Static method, no instance needed

// Generic method invocation
MethodInfo genericMethod = sampleType.GetMethod("GenericMethod");
MethodInfo intGenericMethod = genericMethod.MakeGenericMethod(typeof(int));
int result = (int)intGenericMethod.Invoke(sample, new object[] { 123 });
```

**Advanced Reflection Scenarios:**
```csharp
// Dynamic type creation with Reflection.Emit
public static class DynamicTypeCreator
{
    public static Type CreateDynamicType(string typeName, Dictionary<string, Type> properties)
    {
        AssemblyName assemblyName = new AssemblyName("DynamicAssembly");
        AssemblyBuilder assemblyBuilder = AssemblyBuilder.DefineDynamicAssembly(assemblyName, AssemblyBuilderAccess.Run);
        ModuleBuilder moduleBuilder = assemblyBuilder.DefineDynamicModule("DynamicModule");
        TypeBuilder typeBuilder = moduleBuilder.DefineType(typeName, TypeAttributes.Public | TypeAttributes.Class);
        
        // Add properties
        foreach (var kvp in properties)
        {
            string propertyName = kvp.Key;
            Type propertyType = kvp.Value;
            
            // Create backing field
            FieldBuilder fieldBuilder = typeBuilder.DefineField($"_{propertyName.ToLower()}", propertyType, FieldAttributes.Private);
            
            // Create property
            PropertyBuilder propertyBuilder = typeBuilder.DefineProperty(propertyName, PropertyAttributes.HasDefault, propertyType, null);
            
            // Create getter
            MethodBuilder getterBuilder = typeBuilder.DefineMethod($"get_{propertyName}", 
                MethodAttributes.Public | MethodAttributes.SpecialName | MethodAttributes.HideBySig, 
                propertyType, Type.EmptyTypes);
            
            ILGenerator getterIL = getterBuilder.GetILGenerator();
            getterIL.Emit(OpCodes.Ldarg_0);
            getterIL.Emit(OpCodes.Ldfld, fieldBuilder);
            getterIL.Emit(OpCodes.Ret);
            
            // Create setter
            MethodBuilder setterBuilder = typeBuilder.DefineMethod($"set_{propertyName}",
                MethodAttributes.Public | MethodAttributes.SpecialName | MethodAttributes.HideBySig,
                null, new[] { propertyType });
            
            ILGenerator setterIL = setterBuilder.GetILGenerator();
            setterIL.Emit(OpCodes.Ldarg_0);
            setterIL.Emit(OpCodes.Ldarg_1);
            setterIL.Emit(OpCodes.Stfld, fieldBuilder);
            setterIL.Emit(OpCodes.Ret);
            
            // Associate getter and setter with property
            propertyBuilder.SetGetMethod(getterBuilder);
            propertyBuilder.SetSetMethod(setterBuilder);
        }
        
        return typeBuilder.CreateType();
    }
}

// Usage
var properties = new Dictionary<string, Type>
{
    { "Name", typeof(string) },
    { "Age", typeof(int) },
    { "IsActive", typeof(bool) }
};

Type dynamicType = DynamicTypeCreator.CreateDynamicType("Person", properties);
object dynamicInstance = Activator.CreateInstance(dynamicType);

// Set properties
PropertyInfo nameProperty = dynamicType.GetProperty("Name");
PropertyInfo ageProperty = dynamicType.GetProperty("Age");

nameProperty.SetValue(dynamicInstance, "John Doe");
ageProperty.SetValue(dynamicInstance, 30);

// Get properties
string name = (string)nameProperty.GetValue(dynamicInstance);
int age = (int)ageProperty.GetValue(dynamicInstance);

Console.WriteLine($"Dynamic object: Name={name}, Age={age}");
```

#### Attributes

**Built-in Attributes:**
```csharp
//