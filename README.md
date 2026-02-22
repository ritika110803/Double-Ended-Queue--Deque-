C Program: Deque (Double Ended Queue) Using Array

This project demonstrates how to implement a *Deque (Double Ended Queue)* using a circular array in C.

A deque allows insertion and deletion from *both front and rear ends*.

---

Description

The program:

* Implements a *Deque* using a fixed-size circular array (SIZE = 5)
* Uses two pointers:

  * front
  * rear
* Performs:

  * Insert at Front
  * Insert at Rear
  * Delete from Front
  * Delete from Rear
  * Display
* Handles:

  * Deque Overflow
  * Deque Underflow
* Uses modulo (%) arithmetic for circular behavior

This example is ideal for students learning *Double Ended Queues in Data Structures*.

---

Source Code

c

#include <stdio.h>

#define SIZE 5

int deque[SIZE];

int front = -1;

int rear = -1;

// Check if full

int isFull() {
    return ((rear + 1) % SIZE == front);
}

// Check if empty

int isEmpty() {
    return (front == -1);
}

// Insert at front

void insertFront(int value) {
    
    if (isFull()) {
        printf("Deque is Full!\n");
        return;
    }

    if (isEmpty()) {
        front = rear = 0;
    } else {
        front = (front - 1 + SIZE) % SIZE;
    }

    deque[front] = value;
    printf("Inserted at front: %d\n", value);
}

// Insert at rear

void insertRear(int value) {
    
    if (isFull()) {
        printf("Deque is Full!\n");
        return;
    }

    if (isEmpty()) {
        front = rear = 0;
    } else {
        rear = (rear + 1) % SIZE;
    }

    deque[rear] = value;
    
    printf("Inserted at rear: %d\n", value);
}

// Delete from front

void deleteFront() {
    
    if (isEmpty()) {
        printf("Deque is Empty!\n");
        return;
    }

    printf("Deleted from front: %d\n", deque[front]);

    if (front == rear) {
        front = rear = -1;
    } else {
        front = (front + 1) % SIZE;
    }
}

// Delete from rear

void deleteRear() {
    
    if (isEmpty()) {
        printf("Deque is Empty!\n");
        return;
    }

    printf("Deleted from rear: %d\n", deque[rear]);

    if (front == rear) {
        front = rear = -1;
    } else {
        rear = (rear - 1 + SIZE) % SIZE;
    }
}

// Display deque

void display() {
    
    if (isEmpty()) {
        printf("Deque is Empty!\n");
        return;
    }

    printf("Deque elements: ");
    int i = front;

    while (1) {
        printf("%d ", deque[i]);
        if (i == rear)
            break;
        i = (i + 1) % SIZE;
    }

    printf("\n");
}

// Main function

int main() {
    
    insertRear(10);
    insertRear(20);
    insertFront(5);
    insertFront(2);

    display();

    deleteFront();
    deleteRear();

    display();

    return 0;
}


---

How to Compile and Run

Using GCC

1. Save the file as deque_array.c
2. Open terminal or command prompt
3. Compile the program:


gcc deque_array.c -o deque_array


4. Run the executable:


./deque_array


(On Windows, use deque_array.exe)

---

Sample Output


Inserted at rear: 10
Inserted at rear: 20
Inserted at front: 5
Inserted at front: 2
Deque elements: 2 5 10 20
Deleted from front: 2
Deleted from rear: 20
Deque elements: 5 10


---

Concepts Covered

* Deque (Double Ended Queue)
* Circular array implementation
* Modulo arithmetic
* Overflow and Underflow handling
* Insertion and deletion at both ends

---

How Deque Works

A *Deque* allows:

* Insertion at front and rear
* Deletion from front and rear

Circular behavior ensures:


(rear + 1) % SIZE
(front - 1 + SIZE) % SIZE


This allows efficient reuse of array space.

---

Time Complexity

* *Insert Front:* O(1)
* *Insert Rear:* O(1)
* *Delete Front:* O(1)
* *Delete Rear:* O(1)
* *Display:* O(n)

---

Advantages

* More flexible than Queue
* Efficient circular implementation
* Supports both stack and queue behavior

---

⚠️ Limitations

* Fixed size (SIZE = 5)
* Uses global variables
* No dynamic memory allocation

---
