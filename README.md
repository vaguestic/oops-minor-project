# oops-minor-project
import java.util.Scanner;







// Abstract class for the customer
abstract class Customer {
    String name;
    String address;
    long mobileNumber;
    public Customer(String name, String address, long mobileNumber) {
        this.name = name;
        this.address = address;
        this.mobileNumber = mobileNumber;
    }

    // Abstract method to calculate the electricity bill
    public abstract double calculateBill();
}

// Subclass for residential customers
class ResidentialCustomer extends Customer {
    int unitsConsumed;

    public ResidentialCustomer(String name, String address, long mobileNumber, int unitsConsumed) {
        super(name, address, mobileNumber);
        this.unitsConsumed = unitsConsumed;
    }

    @Override
    public double calculateBill() {
        // Implement the calculation logic for residential customers
        double unitPrice = 0.5; // Price per unit
        return unitsConsumed * unitPrice;
    }
}

// Subclass for commercial customers
class CommercialCustomer extends Customer {
    int unitsConsumed;

    public CommercialCustomer(String name, String address, long mobileNumber, int unitsConsumed) {
        super(name, address, mobileNumber);
        this.unitsConsumed = unitsConsumed;
    }

    @Override
    public double calculateBill() {
        // Implement the calculation logic for commercial customers
        double unitPrice = 0.7; // Price per unit
        return unitsConsumed * unitPrice;
    }
}

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.println("Electricity Billing System");
        System.out.println("Enter customer details:");

        System.out.print("Name: ");
        String name = scanner.nextLine();

        System.out.print("Address: ");
        String address = scanner.nextLine();

        System.out.print("Mobile Number: ");
        long mobileNumber = Long.parseLong(scanner.nextLine());

        System.out.print("Enter units consumed: ");
        int unitsConsumed = Integer.parseInt(scanner.nextLine());

        System.out.print("Residential (R) or Commercial (C) customer? ");
        String customerType = scanner.nextLine();

        Customer customer;

        if (customerType.equalsIgnoreCase("R")) {
            customer = new ResidentialCustomer(name, address, mobileNumber, unitsConsumed);
        } else if (customerType.equalsIgnoreCase("C")) {
            customer = new CommercialCustomer(name, address, mobileNumber, unitsConsumed);
        } else {
            System.out.println("Invalid customer type.");
            return;
        }

        double billAmount = customer.calculateBill();
        System.out.println("Customer Name: " + customer.name);
        System.out.println("Customer Address: " + customer.address);
        System.out.println("Mobile Number: " + customer.mobileNumber);
        System.out.println("Bill Amount: $" + billAmount);

        scanner.close();
    }
}

