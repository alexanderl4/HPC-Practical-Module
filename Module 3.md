### 1. Exploration Instructions Answers

#### Practice 1
1. **Create `mobil3` inside `main()`, fill its attributes, and call `nyalakanMesin()`.**

   **Answer:** We instantiate a new object from the blueprint and assign it specific properties independently from the other objects.
   
```cpp
Mobil mobil3;
mobil3.merk = "Porsche";
mobil3.warna = "Silver";
mobil3.tahun = 2024;
mobil3.nyalakanMesin();
```

#### Practice 2
1. **Add `p1.posisi_x = 100.0;` inside main. Why is it rejected?**

   **Answer:** The compiler rejects it because `posisi_x` is set as **`private`**. Private attributes are locked and strictly cannot be accessed or modified directly from outside the Class (like from `main()`).

3. **Change `private:` to `public:`. Why does it run?**

   **Answer:** Changing it to `public` opens the access gate. The program runs, but this proves a vulnerability: external code can now arbitrarily change coordinate values, ruining the integrity of the simulation math.

#### Practice 3
1. **Change object creation to `Titik2D titikA;` (without values). Why is there an error?**

   **Answer:** Because we defined a custom Constructor that requires two arguments, the default empty constructor no longer exists. C++ throws an error to force the programmer to strictly define the initial coordinates, preventing uninitialized simulation entities.

#### Practice 4: Array of Objects Exploration
1. **Remove `nilai = 0.0;` from the constructor and remove the recording loop. What happens to the final output?**

   **Answer:** The final loop will print **Garbage Values** (random memory numbers) for all sensors. This demonstrates how critical Constructors are. If an entity is generated without an initial state, any batch processing down the line will produce corrupt data.

#### Practice 5: Inheritance Exploration
1. **Change `protected` to `private` in the Base Class. What happens?**

   **Answer:** The program crashes/fails to compile. The Derived Class (`SensorSuhu`) attempts to use `nilai_bacaan`, but because it's now `private`, the Base Class hides it even from its own Child. `protected` is required for Inheritance to work properly.

### 2. Independent Task Answer

```cpp
#include <iostream> // # Includes the iostream library
using namespace std; // # Uses the std namespace

class BankAccount { // # Defines a blueprint (Class) named BankAccount
private: // # Private access to protect data from direct modification outside the class
    double balance; // # Variable to store the amount of money

public: // # Public access for interaction methods (functions)
    // # Constructor to fill the initial balance automatically upon object creation
    BankAccount(double initial_balance) { // # Function with the exact same name as the Class
        balance = initial_balance; // # Assigns the parameter value to the private attribute
    } // # End of Constructor

    void deposit(double amount) { // # Method to add money to the account
        balance += amount; // # Adds the amount to the current balance
        cout << "Deposit $" << amount << " successful. Balance: $" << balance << endl; // # Prints info
    } // # End of deposit method

    void withdraw(double amount) { // # Method to take out money with a safety logic check
        if (amount > balance) { // # Checks if the withdrawal amount exceeds the available balance
            cout << "Withdrawal Failed! Insufficient balance." << endl; // # If yes, print failure message
        } else { // # If the balance is sufficient
            balance -= amount; // # Deducts the amount from the balance
            cout << "Withdrawal $" << amount << " successful. Remaining balance: $" << balance << endl; // # Prints success
        } // # End of if-else block
    } // # End of withdraw method
}; // # End of class definition (don't forget the semicolon)

int main() { // # Main function
    BankAccount myAccount(500.0); // # Creates myAccount object and initializes balance to 500 via Constructor
    
    myAccount.deposit(200.0); // # Calls deposit function, balance becomes 700
    myAccount.withdraw(1000.0); // # Attempts to withdraw 1000 (Should fail)
    myAccount.withdraw(150.0); // # Attempts to withdraw 150 (Should succeed, remaining 550)

    return 0; // # Program finished successfully
} // # End of main function
