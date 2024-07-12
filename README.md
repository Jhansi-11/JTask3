# JTask3
import java.util.Scanner;

public class ATM {
    
    public static class BankAccount {
        private double balance;
    
        public BankAccount(double initialBalance) {
            this.balance = initialBalance;
        }
    
        public double getBalance() {
            return balance;
        }
    
        public void deposit(double amount) {
            if (amount > 0) {
                balance += amount;
                System.out.println("Successfully deposited $" + amount);
            } else {
                System.out.println("Deposit amount must be greater than zero.");
            }
        }
    
        public boolean withdraw(double amount) {
            if (amount > 0 && amount <= balance) {
                balance -= amount;
                System.out.println("Successfully withdrew $" + amount);
                return true;
            } else if (amount <= 0) {
                System.out.println("Withdrawal amount must be greater than zero.");
            } else {
                System.out.println("Insufficient funds. Withdrawal unsuccessful.");
            }
            return false;
        }
    }
    
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        System.out.print("Enter initial balance: $");
        double initialBalance = scanner.nextDouble();
        
        BankAccount account = new BankAccount(initialBalance);
        displayMenu(account, scanner);
        
        scanner.close();
    }
    
    public static void displayMenu(BankAccount account, Scanner scanner) {
        while (true) {
            System.out.println("\nWelcome to the ATM!");
            System.out.println("1. Check Balance");
            System.out.println("2. Deposit");
            System.out.println("3. Withdraw");
            System.out.println("4. Exit");
    
            System.out.print("Choose an option: ");
            int choice = scanner.nextInt();
    
            switch (choice) {
                case 1:
                    System.out.println("Your current balance is: $" + account.getBalance());
                    break;
                case 2:
                    System.out.print("Enter deposit amount: $");
                    double depositAmount = scanner.nextDouble();
                    account.deposit(depositAmount);
                    break;
                case 3:
                    System.out.print("Enter withdrawal amount: $");
                    double withdrawAmount = scanner.nextDouble();
                    account.withdraw(withdrawAmount);
                    break;
                case 4:
                    System.out.println("Thank you for using the ATM. Goodbye!");
                    return;
                default:
                    System.out.println("Invalid choice. Please enter a number between 1 and 4.");
                    break;
            }
        }
    }
}
