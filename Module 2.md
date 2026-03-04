### 1. Exploration Instructions Answers

#### Practice 1
1. **Change `double` to `void`, remove `return`, use `cout` inside the function, and call it without saving to a variable. What is the difference?**

   **Answer:** A `void` function does not return any data to the caller. Instead of sending the calculation result back to `main()`, the function handles the printing (`cout`) internally. In `main()`, we simply trigger the function (`calculateVolume(10.5, 5.0, 2.0);`) and it executes its internal printing block.

#### Practice 2
1. **Add `*ptr_angka = 500;` before `return 0;` and print the original variable. What happens?**

   **Answer:** The value of the original variable `angka` in `main()` automatically changes to **500**. This proves we are directly manipulating the physical memory address. We didn't touch the variable `angka` itself, but we changed the data inside its specific memory slot using the pointer.

#### Practice 3
1. **Remove the `&` symbol on the parameters. Why aren't the values swapped on the screen?**

   **Answer:** Without the `&` symbol, C++ uses **Pass by Value**. This means the function only receives a "photocopy" of the original variables. It successfully swaps the photocopies inside its own scope, but once the function finishes, the photocopies are destroyed. The original variables `x` and `y` in `main()` remain untouched.

#### Practice 4
1. **Change `ukuran` to 6. What happens to the 6th element?**

   **Answer:** The 6th element (index 5) will print a random **Garbage Value**. Since we only assigned 5 numbers, the 6th memory block contains leftover data from other applications previously using that RAM space.

2. **Change the loop condition to `i <= ukuran`. What happens?**

   **Answer:** The program experiences an **Out of Bounds** error. It tries to access memory outside the allocated array. In parallel computing or large programs, this forces the operating system to kill the program instantly (Segmentation Fault).

#### Practice 5
1. **Change the loop order (column `j` outside, row `i` inside). What happens?**

   **Answer:** The matrix is read vertically from top to bottom (**Column-Major Order**). While the output might look mathematically similar, structurally, the computer's memory reader is jumping across different memory blocks rather than reading sequentially. In C++, this makes the computation significantly slower.

### 2. Independent Task Answers

**Task 1: Array Average Function**

```cpp
#include <iostream> // # Includes the input/output library
using namespace std; // # Uses the std namespace

// # Function to calculate average with 2 parameters: an array of doubles and the array size
double calculateAverage(double arr[], int size) { // # Declares the function outside main()
    double total = 0.0; // # Accumulator variable for the total sum
    for (int i = 0; i < size; i++) { // # Loops from the first element to the last element
        total += arr[i]; // # Adds each array element to the total variable
    } // # End of loop
    return total / size; // # Divides the total by the array size to get the average, then returns it
} // # End of function

int main() { // # Main program function
    double data[5] = {10.5, 20.0, 15.5, 30.0, 24.0}; // # Creates an array containing 5 numbers
    
    double result = calculateAverage(data, 5); // # Calls the function and stores its returned value
    cout << "The array average is: " << result << endl; // # Prints the result to the screen
    
    return 0; // # Program finished successfully
} // # End of main function
```

**Task 2: Memory Manipulation with Pointers**

```cpp
#include <iostream> // # Includes the iostream library
using namespace std; // # Uses the std namespace

void squareValue(int *val) { // # Void function accepting a pointer parameter (memory address)
    *val = (*val) * (*val); // # Dereferences the pointer to multiply the memory's content by itself
} // # End of squareValue function

int main() { // # Main function
    int number = 5; // # Declares an integer variable with an initial value of 5
    
    cout << "Initial value : " << number << endl; // # Prints the value before processing
    squareValue(&number); // # Calls the function by passing the MEMORY ADDRESS (&) of the variable
    cout << "Final value   : " << number << endl; // # Prints the value after processing (becomes 25)
    
    return 0; // # Program finished successfully
} // # End of main function
