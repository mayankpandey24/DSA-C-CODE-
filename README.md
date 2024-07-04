# DSA-C-CODE-
#include<stdio.h>
#include<stdlib.h>

int *stack, n, top = - 1;


void push();
void pop();
void peek();
void display();
void resize();

int main()
{
	int choice;
	
	printf("Enter The Number of Element: ");
	scanf("%d", & n);
	stack = (int*)calloc(n, sizeof(int));
	if(stack == NULL)
	{
		printf("Memory allocation failed!!\n");
		return 1;
	}
	
	do
	{
		printf("\nEnter your choice: \n");
		printf("Choice 1: Push\nChoice 2: Peek\nChoice 3: Pop\nChoice 4: Display\nChoice 5: Resize\nChoice 6: Exit\n");
		scanf("%d", & choice);
		
		switch(choice)
		{
			case 1: push();
			break;
			case 2: peek();
			break;
			case 3: pop();
			break;
			case 4: display();
			break;
			case 5: resize();
			break;
			case 6: printf("EXITED!!");
			break;
			default:
				printf("Invalid Input Try(1/2/3/4/5/6):\n");
			
			
		}
			
	}
	while(choice != 0);
	
	return 0;
}

void push() 
{
    int x;
    if (top == n - 1) 
	{
        printf("\nOverflow! Stack is full.\n");
    } 
	else 
	{
        printf("\nEnter the element to be added onto the stack: ");
        scanf("%d", &x);
        top++;
        stack[top] = x;
    }
}
void peek() 
{
    if (top == -1) 
	{
        printf("\nStack is empty.\n");
    } 
	else 
	{
        printf("\nTop element: %d", stack[top]);
    }
}

void pop() 
{
    if (top == -1) 
	{
        printf("\nUnderflow! Stack is empty.");
    } 
	else 
	{
        printf("\nPopped element: %d\n", stack[top]);
        top--;
    }
}

void display() 
{
	int i;
    if (top == -1) 
	{
        printf("\nStack is empty.");
    } 
	else 
	{
        printf("\nElements present in the stack:\n");
        for (i = top; i >= 0; --i) 
		{
            printf("%d\n", stack[i]);
        }
    }
}
void resize() 
{
	
	int temp = n;
	printf("Enter New Size : \n");
	scanf("%d", &n);
	stack = (int*)realloc(stack, n*sizeof(int));
	if(stack==NULL)
	{
        printf("\nMemory reallocation failed. Stack remains unchanged.");
	}
	
	if( n < temp)
	{
		top = n - 1;
	}
}
