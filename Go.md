# ---- [ GO LANGUAGE ] ----

## BUILDING
    go buil Hello.go
        
## HELLO WORLD
```cpp
    package main
    import "fmt"

    func main() {
        fmt.Println("Hello, world")
    }
```

### IMPORT MULTIPLE PACKAGE AT ONCE
```cpp
    import { "fmt"
             "math" 
           }
```

## COMMENTS
```cpp
    // Generate the output         
    /* Multi-line Comments */
```

## VARIABLES 
```cpp
    var i int
    i := 8
// OR
    var i int = 8

// MULTI VARIABLE DECLARATION
    var i,j = 8, 42
    i,j := 8, 42
```
### CONSTANTES
    const pi = 3.14

## OPERATORS
### ARITHMETIC 
```cpp
    // ADDITION         SUBSTRACTION
         x + y            x - y
    // MULTIPLICATION   DIVISION
         x * y            x / y
    // MODULUS(REAMAINDER IF THE DIVISION)
         x % y
    // STRING CONCATENATION
        string = "Hello" + "World"
```

### ASSIGNEMENTS
```cpp
    x = x + y → x += y OR  x *= y for *
```

### RELATIONAL OPERATORS

    1. EQUAL TO (x == y) 
    2. NOT EQUAL TO (x != y)
    3. GREATER THAN ( x > y)
    4. LESS THAN (x < Y)

### LOGICAL OPERATORS
    1. LOGICAL AND (x != y && x <= y)
    2. LOGICAL OR (x != y || x <= y)
    3. LOGICAL NOT (!(x>y))
    4. MULTIPLE COMBINAISON ( (x > 0 && x < 100) || x == 42)

## DATA-TYPES
```cpp
    var x int = 42
    var y float32 = 1.37
    var name string = "James"
    var online bool = true
```

## INPUT
```cpp
    var input string
    // & return adress of variable
    fmt.scanln(&input)

```

## IF STATEMENT
```cpp
    x := 42
    if x > 18 {
        fmt.Println("Allowed")
    } else {
        fmt.Println("Not allowed")
    }

    if x:= 42; x > 18 {
        ...
    }
```

## SWITCH
```cpp
    switch num {
        case 1:
            fmt.Println("One")
        case 2:
            fmt.Println("Two")
        case 3:
            fmt.Println("Three")
        default:
        fmt.Println(num)
    }
```

### CHAIN
```cpp
    switch {
        case x>0 && x<10:
            fmt.Println("Something")
        case x>10:
            fmt.Println("Something else")
    }
```
    
## FOR LOOP
```cpp
    for i:=0; i<5 ; i++ {
        fmt.Println(i)
    }

    for sum <= 1000 {
        res += sum
        sum++
    }
```

## FUNCTIONS
```cpp
    func welcome(name string) {
        fmt.Println("Hello"+name)
    }

    func sum(a , b int) {
        fmt.Println(a+b)
        return a+b
    }

    func concat(a,b string)
        string {
            return a + b
        }

    func swap(x,y int) (int,int) {
        return y, x
    
    func main() {
        welcome()
        result := sum(42+8)
        a,b := swap(42,8) // OUT: 8,42
    }
```

## DEFER 
    A defer statement ensures that the
    function is called only after the surrounding
    functions returns

```cpp
    func welcome() {
        fmt.Println("Welcome")
    }

    func main() {
        defer welcome()
        fmt.Println("Hey")
    }
    // OUT: Hey and after Welcome
    // DEFER is often use for cleanup
    // to release resources used by the code
    // such as files, connections...
```

## SCOPE
