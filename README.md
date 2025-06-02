# CPP MODULE 7 :

# 7a :

# PROGRAM STATEMENT :
Write a CPP Program to insert five do integer elements in to stack using linked list (use STL for 
Stack)

# ALGORITHM :
1. Create an instance of Stack using a list to manage stack operations, and read the number of elements 
(n).
2. Use a loop to read n integers from the user and push them onto the stack.
3. Display the current size and top element of the stack..
4. Perform two pop operations, checking if the stack is empty after each and displaying the new top 
element or a message if the stack is empty.
5. Return from main() to complete execution.

# PROGRAM :
NAME : Viaksh A R
REG NO : 212222040179
```
#include <bits/stdc++.h>
using namespace std;
template <typename T>
class Stack 
{
public:
 list<T> l;
 int cs = 0;
 void push(T d)
 {
 cs++;
 l.push_front(d);
 }
 void pop() 
 {
 if (cs > 0) 
 {
 cs--;
 l.pop_front();
 }
 else
 {
 cout << "Stack empty" << endl;
 }
 }
 bool empty() { return cs == 0; }
 T top() { return l.front(); }
 int size() { return cs; }
 void print() 
 {
 for (auto x : l)
 {
 cout << x << endl;
 }
 }
};
int main()
{
 Stack<int> s;
 int n, x;
 cin >> n;
 for (int i = 0; i < n; i++) 
 {
 cin >> x;
 s.push(x);
 }
 cout << "Current size of the stack is " << s.size() << endl;
 cout << "The top element of the stack is " << s.top() << endl;
 s.pop();
 
 if (!s.empty())
 cout << "The top element after 1 pop operation is " << s.top() << endl;
 s.pop();
 
 if (!s.empty())
 {
 cout << "The top element after 2 pop operations is " << s.top() << endl;
 cout << "Size of the stack after 2 pop operations is " << s.size() << endl;
 } 
 else
 {
 cout << "Stack is now empty." << endl;
 }
 return 0;
}
```

# OUTPUT :
 ![image](https://github.com/user-attachments/assets/fa19326d-dfb2-45ab-b9be-c1804c849c51)

# RESULT :
Thus, The program is verified and executed successfully.The outputs match the expected 
results, confirming its correctness.

# 7b :

# PROGRAM STATEMENT :
Write a CPP program for Infix To Postfix Conversion using Linked List Stack STL

# ALGORITHM :
1. Read the infix expression (string) from the user.
2. Traverse through the infix expression and process each character
3. Use a stack to handle operators and parentheses, following the precedence rules.
4. After processing all characters, pop any remaining operators from the stack to the result string.
5. Print the resulting postfix expression.

# PROGRAM :
```
#include <iostream>
#include<cstring>
#include<stack>
using namespace std;
struct Node
{
 char data;
 struct Node * next;
}*top=NULL;
void Push(char x)
{ struct Node* p=new Node;
 if(p==NULL)
 cout<<"\nStack Overflow";
 else{
 p->data=x;
 p->next=top;
 top=p;
 }
} 
char Pop()
{
 int x=-1;
 struct Node * p;
 if(top==NULL)
 cout<<"\nStack is Empty";
 else{
 p=top;
 x=p->data;
 top = top->next;
 delete p;
 }
 return x;
}
int isEmpty()
{
 return top?0:1;
}
int prec(char ch)
{
 if(ch == '^')
 return 3;
 if(ch == '*' or ch == '/')
 return 2;
 if(ch == '+' or ch == '-')
 return 1;
 return -1;
}
string infixToPostfix(string x)
{
 stack<char> s;
 s.push('A');
 string ans;
 int n = x.length();
 for(int i = 0 ; i < n; i++)
 {
 if((x[i] >= 'a' and x[i] <= 'z') or (x[i] >= 'A' and x[i] <= 'Z'))
 ans += x[i];
 else if(x[i] == '(')
 s.push(x[i]);
 else if(x[i] == ')')
 {
 while(s.top() != 'A' and s.top() != '(')
 {
 ans += s.top();
 s.pop();
 }
 if(s.top() == '(')
 {
 s.pop();
 }
 }
 else
 {
 while(s.top() != 'A' and prec(x[i]) <= prec(s.top()))
 {
 ans += s.top();
 s.pop();
 }
 s.push(x[i]);
 }
 }
 while(s.top() != 'A')
 {
 ans += s.top();
 s.pop();
 }
 return ans;
}
int main()
{
 char *infix = new char;
 cin>>infix;
 cout<<infixToPostfix(infix);
}
```

# OUTPUT :
 ![image](https://github.com/user-attachments/assets/19985485-bb9e-4a94-af3a-5586009dcd8e)

# RESULT :
Thus, The program is verified and executed successfully.The outputs match the expected 
results, confirming its correctness.

# 7c :

# PROGRAM STATEMENT :
Write a CPP Program to implement Queue using Linked List, insert float elements in to Q and 
delete two items from Q.

# ALGORITHM :
1. Define a class or struct to represent a node with data (character) and a pointer to the next node.
2. Create a Queue class with front and rear pointers, and implement enqueue() to insert elements and 
dequeue() to remove elements.
3. In the enqueue() function, create a new node, add it to the end of the queue, and update the rear.
4. In the dequeue() function, remove the node at the front and update the front pointer.
5. In the main function, enqueue multiple float elements, dequeue two items, and display the remaining 
queue.

# PROGRAM :
```
#include<iostream>
using namespace std;
class Node
{
 public:
 float data;
 Node *next;
}*rear,*temp,*front;
void push()
{
 temp = new Node;
 cin>>temp->data;
 temp->next=NULL;
 if(rear == NULL)
 {
 front = temp;
 rear = temp;
 }
 else
 {
 rear->next = temp;
 rear = rear->next;
 }
}
void pop()
{
 if(front == NULL)
 {
 cout<<"Underflow."<<endl;
 }
 
 else
 {
 temp = front;
 front = front->next;
 temp->next=NULL;
 free(temp);
 }
}
void display()
{
 temp = front;
 while(temp!=NULL)
 {
 cout<<temp->data<<" ";
 temp = temp->next;
 }
 cout<<endl;
}
void disp()
{
 temp = front;
 cout<<"Queue Front : "<<temp->data;
 
 while(temp->next!=NULL)
 {
 temp = temp->next;
 }
 cout<<endl;
 cout<<"Queue Rear : "<<temp->data;
}
int main()
{
 int n;
 cin>>n;
 pop();
 for(int i=0;i<n;i++)
 {
 push();
 }
 cout<<"Queue :";
 display();
 pop();
 pop();
 
 cout<<"After DeQueue :";
 display();
 disp();
}
```

# OUTPUT :
 ![image](https://github.com/user-attachments/assets/f546a180-4fb6-472c-9b38-bcb8086da72b)

# RESULT :
Thus, The program is verified and executed successfully.The outputs match the expected 
results, confirming its correctness.

# 7d :

# PROGRAM STATEMENT :
write a C++ program to implement FCFS algorithm(no of.process p1,p2 and p3 and its burst time 
are 10,5 & 8) find out waiting time of the process?

# ALGORITHM :
1. Define the number of processes n and initialize the burst time (bt[]) array.
2. Calculate the waiting time (wt[]) for each process using the formula: wt[i] = bt[i-1] + wt[i-1] for all 
processes except the first.
3. Print the burst time and corresponding waiting time for each process.
4. In the displayWT function, print the process number, burst time, and waiting time for all processes.
5. Return from main() to complete the program execution.

# PROGRAM :
```
#include <iostream>
using namespace std;
void findWT(int bt[], int wt[], int n) 
{
 wt[0] = 0; 
 for (int i = 1; i < n; i++) 
 {
 wt[i] = bt[i - 1] + wt[i - 1];
 }
}
void displayWT( int bt[], int wt[], int n) 
{
 cout << "Processes BT time WT time"<<endl;
 for (int i = 0; i < n; i++)
 {
 cout << " " << i+1 << " " << bt[i] << " " << wt[i] << endl;
 }
}
int main() 
{
 int n = 3;
 int bt[] = {10, 5, 8}; 
 int wt[n]; 
 findWT(bt, wt, n);
 displayWT( bt, wt, n);
 return 0;
}
```

# OUTPUT :
 ![image](https://github.com/user-attachments/assets/14ca44a6-dc07-4714-8113-634af46a161d)

# RESULT :
Thus, The program is verified and executed successfully.The outputs match the expected 
results, confirming its correctness.
