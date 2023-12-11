# STACK-EXERCISE<------JAVA----->
package com.JavaProject;

import java.util.Arrays;
import java.util.InputMismatchException;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        num number = new num();
        number.displayAckerman();

    }
    public static String javaArray(int num){ // Test for fibonacci sequence array
        int values[] = new int[num];
        values[0] = 0;
        values[1] = 1;
        int i = 1;
        while(i < num - 1){
            i += 1;
            values[i] = values[i - 1] + values[i -2];
        }

        return Arrays.toString(values);
    }
    public static class num{ // creating a class called num to perform all the operations necessary for this program
        Scanner input = new Scanner(System.in); // Creating an object called input for accepting user input using the scanner class
        // Factorial
        public void computeFactorial(long num){ // creating the factorial computing method
            long factorial = num; // initialising the factorial value as the number at first instance of the program
            long i = 0L;
            if(num == 0){
                System.out.println(num + "!= " + 1);
            }
            else{
                while(num > (i + 1)){ // while loop for continually generating the value for the factorial
                    i += 1;
                    factorial *= (num - i); // using the formula n! = n x (n-1) x (n-2) x (n-3) x (n-nth)
                }
                System.out.println(num + "!= " + factorial); // printing the factorial as output
            }
        }

        public void displayFactorial(){ // method that asks for the input for the 'computeFactorial' method
            System.out.print("Enter a number: "); // message displayed on the screen asking user for input
            try{ // making sure the program does not break when an error occurs by running the code in the try block
                int number = input.nextInt(); // storing the user's input with type 'int' i.e. 'integer' in a variable called number
                computeFactorial(number); // passing the user's input as an argument for the 'computeFactorial' method
            }catch (InputMismatchException e){ // catching the most possible or common error: 'When user enters a letter instead of a number'
                System.out.println("Invalid Input"); // printing the error message when the error occurs instead of the code breaking and leading to failed execution, those red stuff that show under
            }

        }

        // Ackermann sequence
        public int ackermann(int m, int n){ // creating the ackermann method, from here i no too sabi, just cram am 😅
            if(m == 0){
                return n + 1;
            }
            else if(m > 0 && n==0){
                return ackermann(m - 1, 1);
            }
            else if(m > 0 && n > 0){
                return ackermann(m-1, ackermann(m, n-1));
            }
            return 0;
        }

        public void displayAckerman(){ // creating the method that accepts input for the ackermann method
            try{
                System.out.print("Enter value for m: "); // message displayed on the screen asking user for input
                int num_1 = input.nextInt(); // storing the user's input with type 'int' i.e. 'integer' in a variable called num_1 for the first number in ackermann

                System.out.print("Enter value for n: "); // message displayed on the screen asking user for input
                int num_2 = input.nextInt(); // storing the user's input with type 'int' i.e. 'integer' in a variable called num_2 for the second number in ackermann

                System.out.println("Ackermann("+ num_1 + ", " + num_2 + "): " + ackermann(num_1, num_2)); // passing the user's inputs as arguments for the 'ackermann' method
            }catch (InputMismatchException e){ // catching one of the most possible or common errors: 'When user enters a letter instead of a number'
                System.out.println("Invalid Input"); // printing the error message when the error occurs instead of the code breaking and leading to failed execution, those red stuff that show under
            }catch (StackOverflowError e){ // catching one of the most possible or common errors: 'When the rec'
                System.out.println("Maximum recurrence limit reached!");
            }finally {
                System.out.println("Task Completed!!");
            }

        }

        // Fibonacci Sequence
        public void fibonacci(int num){
            if(num <= 0){
                int[] val ={};
                System.out.println(Arrays.toString(val));
            }
            else if(num == 1){
                int[] val = {0};
                System.out.println(Arrays.toString(val));
            }
            else if(num == 2){
                int[] val = {0, 1};
                System.out.println(Arrays.toString(val));
            }
            else{
                int[] values = new int[num];
                values[0] = 0;
                values[1] = 1;
                int i = 1;
                while(i < num - 1){
                    i += 1;
                    values[i] = values[i - 1] + values[i -2];
                }
                System.out.println(Arrays.toString(values));
            }
        }

        public void displayFibonacci(){
            System.out.print("Enter a the number of values in the fibonacci sequence expected: ");
            int number = input.nextInt();
            fibonacci(number);
        }
    }
}

<-------PYTHON------>
# Factorial
def computeFactorial(num):
    factorial = num
    i = 0
    while(num > (i+1)):
        i += 1
        factorial *= (num - i)
    return factorial

# Factorial Input Function
def factorialApp():
    num = int(input('Enter the number for computing: '))
    print(f'{num}! = {computeFactorial(num)}')


# Ackermann Sequence
def ackermann(m, n):
    if m == 0:
        return n + 1
    elif m > 0 and n == 0:
        return ackermann(m - 1, 1)
    elif m > 0 and n > 0:
        return ackermann(m - 1, ackermann(m, n - 1))

# Ackermann Input Function
def ackermanApp():
    try:
        num1 = int(input('Enter first number: '))
        num2 = int(input('Enter second number: '))
        result = ackermann(num1, num2)
        print(f"Ackermann({num1}, {num2}) =", result)

    except RecursionError:
        print("Maximum Recursion Limit Reached")

    except ValueError:
        print("Invalid Data Type or Invalid Input")
# Function Runner
def run(funtion):
    return funtion

# Fibonacci Sequence
def fibonacci(num):
    if(num <= 0):
        return []
    elif num == 1:
        return [0]
    elif num == 2:
        return [0,1]
    else:
        sequence = [0, 1]
        while len(sequence) < num:
            next_num = sequence[-1] + sequence[-2]
            sequence.append(next_num)
        return sequence

# Fibonacci Input Function
def fibonacciApp():
    length = int(input('Enter the number of values: '))
    print(fibonacci(length))

run(factorialApp())

<------C------->
#include <stdio.h>
#include <stdlib.h>

// Factorial Function
int computeFactorial(int num){
    int factorial = num;
    int i = 0;
    while(num > (i + 1)){
        i += 1;
        factorial *= num - i;
    }
    return factorial;
}

// Ackermann Function
int ackermann(int m, int n){
    if(m == 0){
        return n + 1;
    }
    else if(m > 0 && n==0){
        return ackermann(m-1, 1);
    }
    else if(m > 0 && n > 0){
        return ackermann(m-1, ackermann(m, n-1));
    }
    return 0;
}

// Fibonacci Function
void fibonacci(int num){
    if(num <= 0){
        printf("{}");

    }
    else if(num == 1){
        printf("{ 0 }");
    }
    else if(num == 2){
        printf("{ 0, 1 }");
    }
    else{
        int values[num];
        values[0] = 0;
        values[1] = 1;
        int i = 1;
        while(i < num - 1){
            i += 1;
            values[i] = values[i - 1] + values[ i - 2];
        }
        printf("{ ");
        for(int j = 0; j < num; j++){
            printf("%d, ", values[j]);
        }
        printf("}");
    }
}

int main()
{
//    int number;
//    printf("Enter number to compute: ");
//    scanf("%d", &number);
//    printf("%d! = %d", number, computeFactorial(number));
    fibonacci(8);
    return 0;
}


<--------C++-------->
#include <iostream>

using namespace std;

// Factorial Function
int computeFactorial(int num){
    int factorial = num;
    int i = 0;
    while(num > (i + 1)){
        i += 1;
        factorial *= num - i;
    }
    return factorial;
}

// Ackermann Function
int ackermann(int m, int n){
    if(m == 0){
        return n + 1;
    }
    else if(m > 0 && n == 0){
        return ackermann(m-1, 1);
    }
    else if(m > 0 && n > 0){
        return ackermann(m-1, ackermann(m, n-1));
    }
    return 0;
}

// Fibonacci Function
void fibonacci(int num){
    if(num <= 0){
        cout << "{}";

    }
    else if(num == 1){
        cout << "{ 0 }";
    }
    else if(num == 2){
        cout << "{ 0, 1 }";
    }
    else{
        int values[num];
        values[0] = 0;
        values[1] = 1;
        int i = 1;
        while(i < num - 1){
            i += 1;
            values[i] = values[i - 1] + values[ i - 2];
        }
        cout << "{ ";
        for(int j = 0; j < num; j++){
            cout << values[j] << ", ";
        }
        cout << "}";
    }
}

int main()
{
//    int number;
//    cout << "Enter number to compute: ";
//    cin >> number;
//    cout << number <<"! = " << computeFactorial(number);
    cout << computeFactorial(0);
    return 0;
}


