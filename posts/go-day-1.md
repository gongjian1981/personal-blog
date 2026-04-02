# Practice
1. Install the latest **Go** (*1.26.1*) from the official website [Go Programming Language](https://go.dev/dl/)
2. Install the latest **Visual Studio Code** (*1.114.0*) from the official website [Visual Studio Code - The open source AI code editor](https://code.visualstudio.com/Download)
3. Update **PowerShell** to version *7.6.0* from github [PowerShell/PowerShell: PowerShell for every system!](https://github.com/PowerShell/PowerShell/releases)
4. Open *Visual Studio Code*, Click **Extensions** on the left sidebar, search for 'Go' in the search bar at the top
5. Install the first extension provided by *Go Team at Google*
6. Open *terminal* in *Visual Studio Code* using *PowerShell* and type:
  ```
  go version
  ```

    It will return something like:
  
  ```
  go version go1.26.1 windows/amd64
  ```

7. Create a file named `hello.go` and write the first Go program:
  ```
  package main

  import "fmt"

  func main() {
     fmt.Println("Go installed successfully!")
  }
  ```

8. Press Ctrl + S to save the file.
9. In terminal run command:

   ```go run hello.go```

   It will output:

   ```Go installed successfully!```
   
8. The first Go program is complete.

# Key Concepts
1. There's no semicolon in the code, Go doesn't require semicolons to end statements, the Go compiler automatically inserts them during parsing.
2. package main
   + The keyword `package` is similar to Java's `package`, but in Go it defines a module namespace.
   + Only the `main` package is executable, other packages are used as libraries.
   + In this code, we need to run the code directly, so it has to belong to `package main`
3. import "fmt"
   + The keyword `import` can only be used to import package, since Go has no classes.
4. func main()
   + Go uses the keyword `func` to declare functions. The full syntax is:
  
  ```
    func [receiver] FunctionName[TypeParams](parameters)(returnTypes) {
      // body
    }
  ```

   + If the function name starts with an uppercase letter, it is *public*, if it starts with a lowercase letter, it is *private*.
5. fmt.Println()
   + Call the Println() function from the *fmt* package
