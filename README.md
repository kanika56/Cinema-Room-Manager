# Cinema-Room-Manager
package cinema;

import java.util.Scanner;

public class Cinema {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        textUI(scanner);
        
    }
    public static void textUI(Scanner scanner) {
        System.out.println("Enter the number of rows:");
        int rows = Integer.parseInt(scanner.nextLine());

        System.out.println("Enter the number of seats in each row:");
        int seats = Integer.parseInt(scanner.nextLine());
        String[][] cinema = new String[rows][seats];

        System.out.println("Cinema:");
        System.out.print("  ");
        for (int i = 1; i <= seats; i++) {
            System.out.print(i + " ");
        }
        System.out.println();
        for (int i = 0; i < rows; i++) {
            System.out.print(i + 1 + " ");
            for (int j = 0; j < seats; j++) {
                cinema[i][j] = "S";
                System.out.print(cinema[i][j] + " ");
            }
            System.out.println();
        }
        System.out.println();

        while(true) {
            System.out.println("1. Show the seats");
            System.out.println("2. Buy a ticket");
            System.out.println("3. Statistics");
            System.out.println("0. Exit");

            int expression = Integer.parseInt(scanner.nextLine());
            int n = 0;
            int m = 0;

            if (expression == 1) {
                System.out.println("Cinema:");
                System.out.print("  ");
                for (int i = 1; i <= seats; i++) {
                    System.out.print(i + " ");
                }
                System.out.println();
                for (int i = 0; i < rows; i++) {
                    System.out.print(i + 1 + " ");
                    for (int j = 0; j < seats; j++) {
                        System.out.print(cinema[i][j] + " ");
                    }
                    System.out.println();
                }
            } else if (expression == 2) {
                System.out.println("Enter a row number:");
                int row = Integer.parseInt(scanner.nextLine());

                System.out.println("Enter a seat number in that row:");
                int seat = Integer.parseInt(scanner.nextLine());
                
                
                while (row > rows || seat > seats) {
                    System.out.println("Wrong input!");
                    System.out.println("Enter a row number:");
                    row = Integer.parseInt(scanner.nextLine());
                    System.out.println("Enter a seat number in that row:");
                    seat = Integer.parseInt(scanner.nextLine());
                }
                while (cinema[row - 1][seat - 1] == "B") {
                    System.out.println("That ticket has already been purchased!");
                    System.out.println("Enter a row number:");
                    row = Integer.parseInt(scanner.nextLine());
                    System.out.println("Enter a seat number in that row:");
                    seat = Integer.parseInt(scanner.nextLine());
                    while (row > rows || seat > seats) {
                    System.out.println("Wrong input!");
                    System.out.println("Enter a row number:");
                    row = Integer.parseInt(scanner.nextLine());
                    System.out.println("Enter a seat number in that row:");
                    seat = Integer.parseInt(scanner.nextLine());
                    }
                }
                
                n = row;
                m = seat;
            
                cinema[row - 1][seat - 1] = "B";
                System.out.println("Ticket price: ");
                if (rows * seats <= 60) {
                    System.out.println("$" + 10);
                } else if (row <= rows / 2) {
                    System.out.println("$" + 10);
                    //income += 10;
                } else {
                    System.out.println("$" + 8);
                    //income += 8;
                }
                System.out.println();

            } else if (expression == 3) {
                int tinc = 0;
                int income = 0;
                System.out.print("Number of purchased tickets: ");
                int val = 0;
                for (int i = 0; i < rows; i++) {
                    for (int j = 0; j < seats; j++) {
                        if (cinema[i][j] == "B") {
                            val++;                        }
                    }
                }
                System.out.println(val);
               
                for (int i = 0; i < rows; i++) {
                    for (int j = 0; j < seats; j++) {
                        if (cinema[i][j] == "B") {
                            /*if (rows * seats <= 60) {
                                income += 10;
                            } else*/ 
                            if (i < rows / 2) {
                                income += 10;
                            } else {
                                income += 8;
                            }
                        }
                    }
                }
                int num = rows * seats;
                double num1 = num;
                double val1 = val;
                double temp = val1 / num1 ;
                System.out.printf("Percentage: %.2f%% ", temp * 100);
                System.out.println();
                
                System.out.println("Current income: $" + income);
                System.out.print("Total income: ");
                if (rows * seats <= 60) {
                    System.out.println("$" + rows * seats * 10);
                } else {
                    int x = 0;
                    int y = 0;
                    x = rows / 2 * seats * 10;
                    y = (rows / 2 + 1) * seats * 8;
                    int z = x + y;
                    System.out.println("$" + z);
                }
            
            } else if (expression == 0) {
                break;
            }
        
        }
    }
}
