import java.util.Scanner;
class BankAccount
{
    private double balance;
    public BankAccount(double initialBalance)
    {
        if (initialBalance >= 0)
        {
            this.balance = initialBalance;
        } 
        else
        {
            this.balance = 0;
            System.out.println("Initial balance can't be negative. Setting balance to 0.");
        }
    }
    public void deposit(double amount)
    {
        if (amount > 0) {
            balance=balance+amount;
            System.out.println("Deposited: " + amount);
        } 
        else
        {
            System.out.println("No amount to deposit");
        }
    }
    public void withdraw(double amount) 
    {
        if (amount > 0) 
        {
            if (amount <= balance)
            {
                balance =balance-amount;
                System.out.println("Withdrew: " + amount);
            }
            else
            {
                System.out.println("Insufficient balance.");
            }
        } 
        else 
        {
            System.out.println("Cannot withdraw");
        }
    }
    public double getBalance() 
    {
        return balance;
    }
}
public class BankingSystem {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter initial balance: ");
        double initialBalance = scanner.nextDouble();
        BankAccount account = new BankAccount(initialBalance);
        boolean exit = false;
        while (!exit) 
        {
            System.out.println("\nChoose an operation:");
            System.out.println("1. Deposit");
            System.out.println("2. Withdraw");
            System.out.println("3. Check Balance");
            System.out.println("4. Exit");
            System.out.print("Enter your choice: ");
            int choice = scanner.nextInt();
            switch (choice) 
            {
                case 1:
                    System.out.print("Enter amount to deposit: ");
                    double depositAmount = scanner.nextDouble();
                    account.deposit(depositAmount);
                    break;
                case 2:
                    System.out.print("Enter amount to withdraw: ");
                    double withdrawAmount = scanner.nextDouble();
                    account.withdraw(withdrawAmount);
                    break;
                case 3:
                    System.out.println("Current balance: " + account.getBalance());
                    break;
                case 4:
                    exit = true;
                    System.out.println("Exiting the banking system. Goodbye!");
                    break;
                default:
                    System.out.println("Invalid choice. Please try again.");
                    break;
            }
        }

        scanner.close();
    }
}
