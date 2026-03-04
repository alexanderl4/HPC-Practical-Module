### 1. Exploration Instructions Answers

#### Practice 1
1. **Add `kumpulan_angka.pop_back();`. What happens?**

   **Answer:** The `.pop_back()` method deletes the very last element in the vector. If the last added number was 50, it will be removed, and the vector's `.size()` will shrink to 2.

2. **Add `kumpulan_angka.clear();`. What happens?**

   **Answer:** The `.clear()` method completely wipes out all elements in the vector. The size becomes 0, and the subsequent `for` loop will not execute at all because there is no data left to print.

#### Practice 2: Batch Processing Exploration
1. **Replace the manual `push_back` lines with a `for` loop to dynamically generate 100 tasks.**

   **Answer:** This demonstrates the power of dynamic vectors. You can generate hundreds of objects on the fly:
   
```cpp
// Generate 100 tasks automatically
for(int i = 1; i <= 100; i++) {
    antrean.push_back(TugasKalkulasi(i, i * 2.5, i * 1.5));
}
```

#### Practice 4.1
1. **Change the read file name to "file_salah.txt". What happens?**

   **Answer:** The program safely handles the error. The `if (fileBaca.is_open())` check returns *False*, skipping the reading process, and prints the error message "File tidak ditemukan!" without crashing.

2. **Add 999.9 manually to the text file, comment the writing block, and run.**
   **Answer:** The program acts purely as a reader. It will successfully read the older data along with the manually added "999.9" and print everything to the console, proving it reads real-time external data.

#### Practice 4.2
1. **Add 5 random coordinates manually to the text file and run without changing the C++ code. What happens?**

   **Answer:** The `while (fileBaca >> temp_x >> temp_y)` loop dynamically reads until the end of the file, and the `vector` automatically expands (*auto-resizes*) to fit the 5 new points. The `hasil_jarak.txt` will flawlessly calculate all points without any array size errors.

2. **Modify `hitungJarak()` to use a new reference point, e.g., `(5.0, 5.0)`.**

   **Answer:** The Pythagorean calculation changes to calculate the distance between two specific points rather than from the zero origin.
   
```cpp
void hitungJarak() {
    // Distance formula from point (5.0, 5.0)
    jarak_pusat = std::sqrt((x - 5.0)*(x - 5.0) + (y - 5.0)*(y - 5.0));
}
```

### 2. Independent Task Answer

```cpp
#include <iostream> // # Includes the standard C++ library for terminal input/output
#include <vector> // # Includes the modern library for dynamic arrays (vectors)
#include <fstream> // # Includes the library to read/write external files (txt, csv)
using namespace std; // # Uses the std namespace

int main() { // # The starting point of the program execution
    
    // # 1. Data Structure Initialization
    vector<double> sensor; // # Declares an empty dynamic array (vector) of type double named 'sensor'

    // # 2. Initial Data Insertion
    sensor.push_back(100.5); // # Injects 100.5 into the first element (index 0)
    sensor.push_back(200.0); // # Injects 200.0 into the second element (index 1)
    sensor.push_back(150.5); // # Injects 150.5 into the third element (index 2)

    // # 3. Calibration Process (Batch Processing)
    for (int i = 0; i < sensor.size(); i++) { // # Loops exactly as many times as the vector's dynamic size
        sensor[i] = sensor[i] * 1.1; // # Overwrites the old value with the calibrated value (multiplied by 1.1 / 10% increase)
    } // # End of batch computation block

    // # 4. Saving to External File
    ofstream outputFile("calibration_result.txt"); // # Creates/opens an ofstream object to write to a file
    
    if (outputFile.is_open()) { // # Safety logic: Checks if the file was successfully opened/created
        
        // # 5. Writing Results to the File
        for (int i = 0; i < sensor.size(); i++) { // # Loops again to transfer data from RAM to the Hard Drive File
            outputFile << sensor[i] << "\n"; // # Writes the element's value to the file, followed by a newline (\n) instruction
        } // # End of file writing block
        
        outputFile.close(); // # VERY IMPORTANT: Closes the file access to prevent memory leaks and allow other apps to use it
        cout << "Success! Check the 'calibration_result.txt' file in your project folder.\n"; // # Signals success to the terminal
        
    } else { // # Code block executed if the program lacks permission or fails to create the file
        cout << "Error: Failed to create the file.\n"; // # Prints an error warning message
    } // # End of file safety conditional block

    return 0; // # Exits the program with code 0 (Normal execution)
} // # End of the entire program
```
