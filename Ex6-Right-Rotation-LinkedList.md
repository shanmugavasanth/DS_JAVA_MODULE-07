# Ex6 Right Rotation LinkedList

## DATE:11.11.2025  

### Developed by
**Name:** Shanmuga Vasanth M

**Register Number:** 212223040191 

## AIM:
To write a Java program to:  
- Create a singly linked list.  
- Rotate the linked list to the right by k positions.  
- Display the rotated linked list.  

## Algorithm
1. Start the program.  
2. Create a linked list node class containing `data` and `next`.  
3. Insert elements into the linked list.  
4. Count the number of nodes and make the list circular by connecting the last node to the head.  
5. Find the new head by moving `length - k` steps forward and set the new tail's `next` to `null`.  
6. Display the rotated linked list.  
7. Stop the program.  

## Program:
```java

import java.util.Scanner;

class Node {
    int data;
    Node next;
    Node(int data) {
        this.data = data;
        this.next = null;
    }
}

public class RightRotateLinkedList {
    static Node rotateRight(Node head, int k) {
        if (head == null || k == 0) return head;
        Node temp = head;
        int length = 1;
        while (temp.next != null) {
            temp = temp.next;
            length++;
        }
        temp.next = head;
        k = k % length;
        int stepsToNewHead = length - k;
        Node newTail = temp;
        while (stepsToNewHead-- > 0) {
            newTail = newTail.next;
        }
        Node newHead = newTail.next;
        newTail.next = null;
        return newHead;
    }

    static void display(Node head) {
        Node temp = head;
        while (temp != null) {
            System.out.print(temp.data + " ");
            temp = temp.next;
        }
        System.out.println();
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        Node head = null, tail = null;
        System.out.print("Enter number of elements: ");
        int n = sc.nextInt();
        System.out.println("Enter elements:");
        for (int i = 0; i < n; i++) {
            int val = sc.nextInt();
            Node newNode = new Node(val);
            if (head == null) {
                head = tail = newNode;
            } else {
                tail.next = newNode;
                tail = newNode;
            }
        }
        System.out.print("Enter k (positions to rotate): ");
        int k = sc.nextInt();
        head = rotateRight(head, k);
        System.out.println("Linked list after right rotation:");
        display(head);
        sc.close();
    }
}
```
## OUTPUT

<img width="940" height="205" alt="511968122-2bf22511-0bc0-448b-b9ad-b8351307e479" src="https://github.com/user-attachments/assets/740f620a-26f0-4a8b-be6f-69a723d105e7" />

## RESULT
Thus, the Java program to perform right rotation on a linked list is implemented successfully.
