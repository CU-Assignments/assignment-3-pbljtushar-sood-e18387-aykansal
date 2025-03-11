## Solution 1: SquareRootCalculator.java

```java
import java.util.Scanner;

public class SquareRootCalculator {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        System.out.print("Enter a number: ");
        try {
            double number = Double.parseDouble(scanner.nextLine());
            if (number < 0) {
                throw new IllegalArgumentException("Cannot calculate the square root of a negative number.");
            }
            double result = Math.sqrt(number);
            System.out.println("Square root: " + result);
        } catch (NumberFormatException e) {
            System.out.println("Error: Invalid input. Please enter a numeric value.");
        } catch (IllegalArgumentException e) {
            System.out.println("Error: " + e.getMessage());
        }
        
        scanner.close();
    }
}
```

## Solution 2: ATMWithdrawal.java
```java
import java.util.Scanner;

class InvalidPinException extends Exception {
    public InvalidPinException(String message) {
        super(message);
    }
}

class InsufficientBalanceException extends Exception {
    public InsufficientBalanceException(String message) {
        super(message);
    }
}

public class ATMWithdrawal {
    private static final int CORRECT_PIN = 1234;
    private static double balance = 3000; // Initial balance

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        try {
            System.out.print("Enter PIN: ");
            int pin = Integer.parseInt(scanner.nextLine());
            if (pin != CORRECT_PIN) {
                throw new InvalidPinException("Invalid PIN.");
            }
            
            System.out.print("Withdraw Amount: ");
            double amount = Double.parseDouble(scanner.nextLine());
            if (amount > balance) {
                throw new InsufficientBalanceException("Insufficient balance. Current Balance: " + balance);
            }
            
            balance -= amount;
            System.out.println("Withdrawal successful! Current Balance: " + balance);
        } catch (NumberFormatException e) {
            System.out.println("Error: Invalid input. Please enter numeric values.");
        } catch (InvalidPinException | InsufficientBalanceException e) {
            System.out.println("Error: " + e.getMessage());
        } finally {
            System.out.println("Thank you for using the ATM.");
        }
        
        scanner.close();
    }
}
```

## Solution 3: UniversityEnrollment.java
```java
import java.util.Scanner;

class CourseFullException extends Exception {
    public CourseFullException(String message) {
        super(message);
    }
}

class PrerequisiteNotMetException extends Exception {
    public PrerequisiteNotMetException(String message) {
        super(message);
    }
}

public class UniversityEnrollment {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        try {
            System.out.print("Enroll in Course: ");
            String course = scanner.nextLine();
            System.out.print("Prerequisite: ");
            String prerequisite = scanner.nextLine();
            System.out.print("Status (completed/not completed): ");
            String status = scanner.nextLine().toLowerCase();
            
            if (course.equalsIgnoreCase("Advanced Java")) {
                if (!status.equals("completed")) {
                    throw new PrerequisiteNotMetException("Complete " + prerequisite + " before enrolling in " + course + ".");
                }
                // Simulate a full course for demonstration
                throw new CourseFullException("The course " + course + " is full.");
            }
            
            System.out.println("Enrollment successful for " + course);
        } catch (CourseFullException | PrerequisiteNotMetException e) {
            System.out.println("Error: " + e.getMessage());
        }
        
        scanner.close();
    }
}
```