#include <stdio.h>
#define R1 2 // Number of rows in the first matrix
#define C1 3 // Number of columns in the first matrix (and rows in the second)
#define C2 2 // Number of columns in the second matrix
int main() {
 int a[R1][C1] = {{1, 2, 3}, {4, 5, 6}}; // First matrix
 int b[C1][C2] = {{1, 2}, {3, 4}, {5, 6}}; // Second matrix
 int c[R1][C2]; // Resultant matrix of dimensions R1 x C2
 int i, j, k;
 // Matrix multiplication logic
 for (i = 0; i < R1; i++) {
 for (j = 0; j < C2; j++) {
 c[i][j] = 0; // Initializing elements of matrix c to 0
 for (k = 0; k < C1; k++) {
 c[i][j] += a[i][k] * b[k][j];
 }
 }
 }
 // Printing the result matrix c
 printf("Result of matrix multiplication:\n");
 for (i = 0; i < R1; i++) {
 for (j = 0; j < C2; j++) {
 printf("%d ", c[i][j]);
 }
 printf("\n");
 }
 return 0;
}
...................................................................
#include <stdio.h>
// Function prototypes
void showMenu();
void checkBalance(float balance);
void depositMoney(float *balance);
void withdrawMoney(float *balance);
int main() {
 float balance = 0.0f; // Initial balance
 int option;
 while (1) {
 showMenu();
 printf("Choose an option: ");
 scanf("%d", &option);
 switch (option) {
 case 1:
 checkBalance(balance);
 break;
 case 2:
 depositMoney(&balance);
 break;
 case 3:
 withdrawMoney(&balance);
 break;
 case 4:
 printf("Exiting the banking application.\n");
 return 0;

 default:
 printf("Invalid option. Please try again.\n");
 }
 }
 return 0;
}
void showMenu() {
 printf("\n*** Banking Application Menu ***\n");
 printf("1. Check Balance\n");
 printf("2. Deposit Money\n");
 printf("3. Withdraw Money\n");
 printf("4. Exit\n");
}
void checkBalance(float balance) {
 printf("Your current balance is:Rs.%.2f\n", balance);
}
void depositMoney(float *balance) {
 float amount;
 printf("Enter amount to deposit: ");
 scanf("%f", &amount);
 if (amount > 0) {
 *balance += amount;
 printf("Successfully depositedRs.%.2f\n", amount);
 printf("New balance is:Rs.%.2f\n", *balance);
 } else {
 printf("Invalid amount. Please enter a positive number.\n");
 }
}
void withdrawMoney(float *balance) {
 float amount;
 printf("Enter amount to withdraw: ");
 scanf("%f", &amount);
 if (amount > 0 && amount <= *balance) {
 *balance -= amount;
 printf("Successfully withdrewRs.%.2f\n", amount);
 printf("New balance is:Rs.%.2f\n", *balance);

 } else if (amount > *balance) {
 printf("Insufficient balance to withdraw that amount.\n");
 } else {
 printf("Invalid amount. Please enter a positive number.\n");
 }
}
..................................................................................................
#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>
#define PIN 1234
#define INITIAL_BALANCE 1000.0
void check_balance(double balance) {
 printf("Your current balance is: $%.2f\n", balance);
}
void withdraw(double *balance) {
 double amount;
 printf("Enter the amount to withdraw: ");
 scanf("%lf", &amount);
 if (amount > *balance) {
 printf("Insufficient balance!\n");
 } else {
 *balance -= amount;
 printf("Please take your cash. Your new balance is: $%.2f\n", *balance);
 }
}
void deposit(double *balance) {
 double amount;
 printf("Enter the amount to deposit: ");
 scanf("%lf", &amount);
 *balance += amount;

 printf("Your new balance is: $%.2f\n", *balance);
}
int main() {
 int userPin, option;
 double balance = INITIAL_BALANCE;
 bool authenticated = false;
 printf("Welcome to the ATM!\n");
 while (!authenticated) {
 printf("Please enter your PIN: ");
 scanf("%d", &userPin);
 if (userPin == PIN) {
 authenticated = true;
 } else {
 printf("Incorrect PIN. Try again.\n");
 }
 }
 do {
 printf("\nATM Menu:\n");
 printf("1. Check Balance\n");
 printf("2. Withdraw Cash\n");
 printf("3. Deposit Cash\n");
 printf("4. Exit\n");
 printf("Choose an option: ");
 scanf("%d", &option);
 switch (option) {
 case 1:
 check_balance(balance);
 break;
 case 2:
 withdraw(&balance);
 break;
 case 3:
 deposit(&balance);
 break;
 case 4:
 printf("Thank you for using the ATM. Goodbye!\n");
 break;
 default:
 printf("Invalid option. Please try again.\n");
 break;
 }
 } while (option != 4);
 return 0;

}
