# Internpedia-task-2
# ATM Interface 
# code:
import java.util.Scanner;

// User Account Class:
class UserAccount {
    private int balance;

    public UserAccount(int initialBalance) {
        balance = initialBalance;
    }

    public int getBalance() {
        return balance;
    }

    public void deposit(int amount) {
        if (amount > 0) {
            balance += amount;
            System.out.println("Deposited: $" + amount);
        } else {
            System.out.println("Invalid deposit amount!");
        }
    }

    public boolean withdraw(int amount) {
        if (amount <= balance && amount > 0) {
            balance -= amount;
            System.out.println("Withdrawn: $" + amount);
            return true;
        } else {
            System.out.println("Insufficient funds or invalid amount!");
            return false;
        }
    }
}

// ATM Class:
public class ATMAYUSH {
    private UserAccount userAccount;

    public ATMAYUSH(UserAccount userAccount) {
        this.userAccount = userAccount;
    }

    public void withdraw(int amount) {
        if (amount > 0) {
            if (userAccount.withdraw(amount)) {
                System.out.println("Remaining Balance: $" + userAccount.getBalance());
            }
        } else {
            System.out.println("wrong withdrawal amount!");
        }
    }

    public void deposit(int amount) {
        if (amount > 0) {
            userAccount.deposit(amount);
            System.out.println("Remaining Balance: $" + userAccount.getBalance());
        } else {
            System.out.println("wrong deposit amount!");
        }
    }

    public void checkBalance() {
        System.out.println("Current Balance: $" + userAccount.getBalance());
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("Welcome to the ATMAYUSH!");

        // Initialize user's account with $1000
        UserAccount userAccount = new UserAccount(1000);

        ATMAYUSH atmayush = new ATMAYUSH(userAccount);

        while (true) {
            System.out.println("\nChoose an option:");
            System.out.println("1. Withdraw");
            System.out.println("2. Deposit");
            System.out.println("3. Check Balance");
            System.out.println("4. Exit");

            int choice;
            try {
                choice = scanner.nextInt();
            } catch (Exception e) {
                System.out.println("wrong input! Please enter a number.");
                scanner.nextLine(); // Clear input buffer
                continue;
            }

            switch (choice) {
                case 1:
                    System.out.println("Enter amount to withdraw:");
                    int withdrawAmount = scanner.nextInt();
                    atmayush.withdraw(withdrawAmount);
                    break;
                case 2:
                    System.out.println("Enter amount to deposit:");
                    int depositAmount = scanner.nextInt();
                    atmayush.deposit(depositAmount);
                    break;
                case 3:
                    atmayush.checkBalance();
                    break;
                case 4:
                    System.out.println("Thank you Ayush for using the ATM!");
                    scanner.close();
                    System.exit(0);
                default:
                    System.out.println("wrong choice Ayush! Please Try again.");
            }
        }
    }
}


