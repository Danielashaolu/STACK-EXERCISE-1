   #include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <ctype.h>

// Node structure for the stack
struct Node {
    char data;
    struct Node* next;
};

// Function to initialize an empty stack
struct Node* initializeStack() {
    return NULL;
}

// Function to push a character onto the stack
void push(struct Node** top, char data) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    if (newNode == NULL) {
        printf("Memory allocation error\n");
        exit(EXIT_FAILURE);
    }

    newNode->data = data;
    newNode->next = *top;
    *top = newNode;
}

// Function to pop a character from the stack
char pop(struct Node** top) {
    if (*top == NULL) {
        printf("Stack underflow\n");
        exit(EXIT_FAILURE);
    }

    char data = (*top)->data;
    struct Node* temp = *top;
    *top = (*top)->next;
    free(temp);

    return data;
}

// Function to check if a string is a palindrome
int isPalindrome(char* str) {
    struct Node* stack = initializeStack();

    // Push each character onto the stack
    for (int i = 0; i < strlen(str); i++) {
        char c = tolower(str[i]);
        if (isalpha(c)) {
            push(&stack, c);
        }
    }
// Pop each character and compare with the original string
    for (int i = 0; i < strlen(str); i++) {
        char c = tolower(str[i]);
        if (isalpha(c)) {
            if (c != pop(&stack)) {
                return 0; // Not a palindrome
            }
        }
    }

    return 1; // Palindrome
}

int main() {
    char input[100];

    printf("Enter a string: ");
    fgets(input, sizeof(input), stdin);

    // Remove newline character from the input
    input[strcspn(input, "\n")] = '\0';

    if (isPalindrome(input)) {
        printf("The string is a palindrome.\n");
    } else {
        printf("The string is not a palindrome.\n");
    }

    return 0;
    }
