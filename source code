#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX_SIZE 100

struct Stack {
    int top;
    char items[MAX_SIZE];
};

void initStack(struct Stack *s) {
    s->top = -1;
}

int isEmpty(struct Stack *s) {
    return s->top == -1;
}

void push(struct Stack *s, char c) {
    if (s->top == MAX_SIZE - 1) {
        printf("Error: Stack overflow\n");
        exit(EXIT_FAILURE);
    }
    s->items[++(s->top)] = c;
}

char pop(struct Stack *s) {
    if (isEmpty(s)) {
        printf("Error: Stack underflow\n");
        exit(EXIT_FAILURE);
    }
    return s->items[(s->top)--];
}

char peek(struct Stack *s) {
    if (isEmpty(s)) {
        printf("Error: Stack is empty\n");
        exit(EXIT_FAILURE);
    }
    return s->items[s->top];
}

int isBalanced(char *s) {
    struct Stack stack;
    initStack(&stack);
    int i, n = strlen(s);
    for (i = 0; i < n; i++) {
        if (s[i] == '(' || s[i] == '{' || s[i] == '[') {
            push(&stack, s[i]);
        } else if (s[i] == ')' || s[i] == '}' || s[i] == ']') {
            if (isEmpty(&stack)) {
                return 0; // Tidak ada tanda kurung pembuka yang sesuai
            }
            char top = pop(&stack);
            if ((s[i] == ')' && top != '(') ||
                (s[i] == '}' && top != '{') ||
                (s[i] == ']' && top != '[')) {
                return 0; // Tanda kurung tidak berpasangan
            }
        }
    }
    return isEmpty(&stack); // Stack harus kosong untuk urutan yang seimbang
}

int main() {
    char input[MAX_SIZE];
    printf("Masukkan urutan tanda kurung: ");
    fgets(input, MAX_SIZE, stdin);
    input[strcspn(input, "\n")] = '\0'; // Menghilangkan karakter newline dari input
    if (isBalanced(input)) {
        printf("YES\n");
    } else {
        printf("NO\n");
    }
    return 0;
}
