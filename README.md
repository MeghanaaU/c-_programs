#include <stdio.h>
#define MAX 5

void push(int stack[], int *top, int value) {
    if (*top >= MAX - 1) {
        printf("Stack overflow: cannot push\n");
        return;
    }
    *top = *top + 1;
    stack[*top] = value;
    printf("Pushed the value %d to the stack\n", value);
}

void pop(int stack[], int *top) {
    if (*top == -1) {
        printf("Stack underflow: cannot pop\n");
        return;
    }
    printf("Popped the value %d\n", stack[*top]);
    *top = *top - 1;
}

void display(int stack[], int *top) {
    if (*top == -1) {
        printf("Nothing to display\n");
        return;
    }
    printf("Stack elements: ");
    for (int i = 0; i <= *top; i++) {
        printf("%d ", stack[i]);
    }
    printf("\n");
}

int main() {
    int stack[MAX];
    int top = -1;
    int value, choice;

    do {
        printf("Enter your choice (1 to push, 2 to pop, 3 to display, 4 to exit): ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                printf("Enter value to push: ");
                scanf("%d", &value);
                push(stack, &top, value);
                break;

            case 2:
                pop(stack, &top);
                break;

            case 3:
                display(stack, &top);
                break;

            case 4:
                printf("Exiting...\n");
                break;

            default:
                printf("Invalid choice\n");
        }
    } while (choice != 4);

    return 0;
}
