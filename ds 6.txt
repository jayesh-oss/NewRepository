#include <stdio.h>
#include <conio.h>
#include <stdlib.h>
struct Node {
int data;
struct Node* next;
};
struct Node* head = NULL;
void insertAtBeginning(int data) {
struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
newNode->data = data;
newNode->next = head;
head = newNode;
}
void insertAtEnd(int data) {
struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
newNode->data = data;
newNode->next = NULL;
if (head == NULL) {
head = newNode;
} else {
struct Node* temp = head;
while (temp->next != NULL) {
temp = temp->next;
}
temp->next = newNode;
}
}
void deleteAtBeginning() {
if (head == NULL) {
printf("Linked list is empty. Cannot delete.\n");
} else {
struct Node* temp = head;
head = head->next;
free(temp);
}
}
void deleteAtEnd() {
if (head == NULL) {
printf("Linked list is empty. Cannot delete.\n");
} else if (head->next == NULL) {
free(head);
head = NULL;
} else {
struct Node* temp = head;
while (temp->next->next != NULL) {
temp = temp->next;
}
free(temp->next);
temp->next = NULL;
}
}
void display() {
struct Node* temp = head;
if (temp == NULL) {
printf("Linked list is empty.\n");
} else {
printf("Linked list elements: ");
while (temp != NULL) {
printf("%d -> ", temp->data);
temp = temp->next;
}
printf("NULL\n");
}
}
int main() {
int choice, data;
do {
printf("\nLinked List Menu:\n");
printf("1. Insert at the Beginning\n");
printf("2. Insert at the End\n");
printf("3. Delete at the Beginning\n");
printf("4. Delete at the End\n");
printf("5. Display\n");
printf("6. Exit\n");
printf("Enter your choice: ");
scanf("%d", &choice);
switch (choice) {
case 1:
printf("Enter data to insert at the beginning: ");
scanf("%d", &data);
insertAtBeginning(data);
break;
case 2:
printf("Enter data to insert at the end: ");
scanf("%d", &data);
insertAtEnd(data);
break;
case 3:
deleteAtBeginning();
break;
case 4:
deleteAtEnd();
break;
case 5:
display();
break;
case 6:
exit(0);
default:
printf("Invalid choice. Please try again.\n");
}
} while (choice != 6);
return 0;
}