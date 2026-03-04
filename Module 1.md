1. Exploration Instructions Answers
Practice 1 (for loop):  If int i = 0: The sum result doesn't change (because you are just adding 0), but the loop will run 1 extra time.

If i += 2 (limit 10): The program only adds the odd numbers (1, 3, 5, 7, 9), making the total 25.

If = 0 is removed: The variable will grab a random value from the computer's leftover memory (garbage value), making the final addition completely incorrect/random.

Practice 2 (while loop):  If int number = 10;: The program will finish immediately without asking for any input. Why? Because the while loop checks the condition number < 0 at the very beginning. Since 10 is not less than 0 (false), the loop block is skipped entirely.

Practice 3 (do-while to while):  The main logical difficulty is that we must provide a "dummy initial value" (e.g., char choice = 'Y';) before the while loop. If we don't, the system will evaluate the condition as false immediately and refuse to execute the code block inside the loop.

2. Independent Task Answer

#include <iostream> // # Includes the standard library for input (cin) and output (cout) functions
using namespace std; // # Uses the standard namespace so we don't have to type std:: repeatedly

int main() { // # The main function, the starting point of the program execution
    int number; // # Declares a variable to store the number inputted by the user
    int total_positive = 0; // # Variable to count the amount of positive numbers, strictly initialized to 0

    // # 1. Ask the user to input exactly 5 numbers using a for loop
    for (int i = 1; i <= 5; i++) { // # The loop runs exactly 5 times (from 1 to 5)
        cout << "Enter number " << i << ": "; // # Prints the instruction to the screen
        cin >> number; // # Receives the typed input and stores it in the 'number' variable

        // # 2. Check if the number is positive, negative, or zero using if-else
        if (number > 0) { // # Condition 1: If the number is greater than 0 (Positive)
            cout << "-> Status: Positive\n"; // # Print the Positive status to the screen
            // # 3. Count the total of positive numbers
            total_positive++; // # Add 1 to total_positive (same as total_positive = total_positive + 1)
        } 
        else if (number < 0) { // # Condition 2: If condition 1 is false, check if it's less than 0 (Negative)
            cout << "-> Status: Negative\n"; // # Print the Negative status to the screen
        } 
        else { // # Condition 3: If it's not greater than 0 and not less than 0, it must be 0
            cout << "-> Status: Zero\n"; // # Print the Zero status to the screen
        } // # End of the conditional checking block
    } // # End of the for loop block

    // # 4. Print the final result after the loop finishes
    cout << "\nTotal positive numbers entered: " << total_positive << endl; // # Display the accumulated total of positive numbers

    return 0; // # Tells the operating system that the program has finished without errors
} // # End of the main function
