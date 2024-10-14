PROBLEM TITLE: Make all negative in one end
AIM:
To write a program to arrange the positive and negative numbers such that all negative numbers appear before all positive numbers.
PROBLEM DESCRIPTION:
Radhika has a basket of balls which are numbered with both positive and negative numbers in random order. She wants to rearrange the balls so that all negative number balls appear before all positive number balls with the order maintained. As she is busy with her homework, help her to complete the task. Write a program to implement the above task using array. Perform the basic operations includes creating an array, inserting an element in an array, displaying elements of array.
INPUT FORMAT:
The first line contains the number of balls: n
The second line contains the positive and negative numbers: nums
OUTPUT FORMAT:
Print the numbers so that all negative numbers appear before all positive numbers
CONSTRAINTS:
2 <= n <= 2 * 105
1 <= |nums[i]| <= 105
TEST CASE 1:
Input:
3
1 -2 3
Output:
-2 1 3
TEST CASE 2:
Input:
5
-3 -5 9 6 -1
Output:
-3 -5 -1 9 6
TEST CASE 3:
Input:
7
1 -2 -3 4 5 -6 9
Output:
-2 -3 -6 1 4 5 9
ALGORITHM:
Pass the given array to the function to rearrange the array elements.
Iterate through the array and find the negative element in the array and insert it within the array in the sequence of 0 to n-1 by shifting the positive element one position to the right.
If the encountered element is positive, then skip it and move on to the next element. 
The rearranged array is displayed on the console.

SOURCE CODE:
#include <stdio.h>
void rearrangePositiveNegativeElements(int arr[], int size){
int i, temp, j;
for(i = 1; i < size; i++){
temp = arr[i];
if (temp > 0)
continue;
    j = i - 1;
    while(j >=0 && arr[j] > 0){
        arr[j + 1] = arr[j];
        j--;
    }

    arr[j + 1] = temp;
}
}
int main(){
int numElements, i;
printf("Enter the number of elements: \n");
scanf("%d", &numElements);
int myArray[numElements];
printf("Enter the array elements: \n");
for(i = 0; i < numElements; i++){
scanf("%d", &myArray[i]);
}
printf("Original array is: \n");
for(i = 0; i < numElements; i++){
    printf("%d ", myArray[i]);
}
printf("\n");
rearrangePositiveNegativeElements(myArray, numElements);
printf("Rearranged array is: \n");
for(i = 0; i < numElements; i++){
    printf("%d ", myArray[i]);
}
printf("\n");
return 0;
}

SAMPLE INPUT:
Enter the number of elements:
5
Enter the array elements:
1 -2 3 4 -5

SAMPLE OUTPUT:
Original array is:
1 -2 3 4 -5
Rearranged array is:
-2 -5 1 3 4
OUTPUT SCREENSHOTS: 


RESULT:
Thus, the C program to arrange the positive and negative numbers such that all negative numbers appear before all positive numbers is implemented and verified successfully. 




TASK NO: 1B
TASK NAME: Finding Duplicates
PROBLEM TITLE: Storing Student ID ensuring Data Uniqueness
AIM:
To write a program to find the duplicate entry of student Id using array concept.
PROBLEM DESCRIPTION:
You are working on storing the student id in a database. There is a requirement to ensure that no duplicate entries of student id are allowed. Write a program to print all the duplicate student id that occurs more than once. Return the duplicate id in ascending order. If there is no duplicate id, then print -1.
INPUT FORMAT:
The first line represents number of students - n
Second line represents the list of Student Id - id 
OUTPUT FORMAT:
Print the student id removing the duplicates
CONSTRAINTS:
1 <= n <= 1000
1 <= nums <=2000
TEST CASE 1:
Input:
4
1 4 5 6
Output:
-1
TEST CASE 2:
Input:
5
2 3 1 2 3
Output:
2 3

TEST CASE 3:
Input:
6
103 100 200 103 100 201
Output:
100 103


ALGORITHM:
We iterate through the array using two nested loops to compare each element with every other element in the array. 
If an element appears more than once, we insert it into the set. 
The repeating variable is used to keep track of whether an element has already been inserted into the set. 
Once a repeating element is found, we break out of the inner loop to avoid inserting it multiple times.

SOURCE CODE:
#include <stdio.h>
#include <stdlib.h>

int* duplicates(int arr[], int n, int* result_size) {
    int* ans = NULL;
    int i;

    // Sorting the array
    for (i = 0; i < n-1; i++) {
        for (int j = i + 1; j < n; j++) {
            if (arr[i] > arr[j]) {
                int temp = arr[i];
                arr[i] = arr[j];
                arr[j] = temp;
            }
        }
    }

    // Finding duplicates
    for (i = 1; i < n; i++) {
        if (arr[i] == arr[i - 1] && arr[i] != arr[i + 1]) {
            // Adding the duplicate element to the ans array
            (*result_size)++;
            ans = (int*)realloc(ans, (*result_size) * sizeof(int));
            ans[(*result_size) - 1] = arr[i];
        }
    }

    if (*result_size) {
        return ans;
    } else {
        free(ans);
        return NULL;
    }
}
int main()
{
    int num;
    int arr[10];
    printf("enter the number of ids:");
    scanf("%d",&num);
    printf("Enter the id's:");
    for(int i=0;i<num;i++)
    {

        scanf("%d",&arr[i]);
    }

    //int n = sizeof(arr) / sizeof(arr[0]);
    int result_size = 0;
    int* result = duplicates(arr, num, &result_size);

    if (result != NULL) {
        printf("Duplicate elements are: ");
        for (int i = 0; i < result_size; i++) {
            printf("%d ", result[i]);
        }
        free(result);
    } else {
        printf("-1");
    }

    return 0;
}

SAMPLE INPUT:
enter the number of ids:5
Enter the id’s:100 201 203 100 400
SAMPLE OUTPUT:
Duplicate elements are: 100

OUTPUT SCREENSHOTS: 






























RESULT:
Thus, the C program to program to find the duplicate entry of student Id using array concept is implemented and verified successfully. 

TASK NO: 1C
TASK NAME: Missing Element
PROBLEM TITLE: Tracking missing inventory system
AIM:
To write a program to identify any missing items in the inventory using array concept.
PROBLEM DESCRIPTION:
Assume, you are working on an inventory management system for a retail store. The system keeps track of the available inventory items by storing their unique identifiers in an array. However, there is a need to identify the missing items in the inventory. Your task is to ensure accurate inventory management and avoid stock discrepancies, and to identify the missing product IDs with in the specified range.
INPUT FORMAT:
The first line contains the number of items : n
The second line array of  n items
The third and forth line represents the range start and end
OUTPUT FORMAT:
Return an array of all missing item numbers. Else print -1
CONSTRAINTS:
1 <= n <= 105
1 <= q <= n
1 <= nums[i] <= n
TEST CASE 1:
Input:
5
4 3 7 8 2 1
1
8
Output: 
5 6

TEST CASE 2:
Input: 
5
1 2 3 4 5
1
5
Output:
-1

TEST CASE 3:
Input:
2
1 4
1 5	
Output:
2 3 5	

ALGORITHM:
Create a temp array temp[] of size n + 1 with all initial values as 0.
Traverse the input array arr[], and do following for each arr[i] 
if(temp[arr[i]] == 0) temp[arr[i]] = 1 
Traverse temp[] and output the array element having value as 0 (This is the missing element).

SOURCE CODE:
#include<stdio.h>
int main()
{
    int n,i,sum=0,c,start,end,noMissing=0;
    printf("\nEnter number of elements in an array:");
    scanf("%d",&n);
    int a[n];
    printf("\nEnter %d elements in array:\n",n);
    for(i = 0;i < n;i++)
    {
        scanf("%d",&a[i]);
    }
    printf("\nEnter Start and End values:\n");
    scanf("%d\n%d",&start,&end);
    printf("\nMissing elements in a range of %d to %d :\n",start,end);
    while(start<=end)
    {
    	c=0;
    	for(i = 0;i < n;i++)
    	{
    		if(start==a[i])
    		{
    			c=1;
    			break;
			}
		}
		if(c==0)
		{
			printf("%d ",start);
			noMissing=1;
		}
		start++;
	}
	if(noMissing==0)
		printf("\-1");
}
SAMPLE INPUT:
Enter number of elements in an array:5

Enter 5 elements in array:
1
4
3
6
5

Enter Start and End values:
1
8

SAMPLE OUTPUT:
Missing elements in a range of 1 to 8 :
2 7 8
OUTPUT SCREENSHOTS: 


RESULT:
Thus, the C program to program to find the missing items in the inventory using array concept is implemented and verified successfully. 

TASK NO: 1D
TASK NAME: Minimum Difference
PROBLEM TITLE: Optimal Buying and Selling point
AIM:
To write a program to calculate the minimum difference between stock prices to find the optimal buying and selling points.
PROBLEM DESCRIPTION:
Imagine, you have a list of stock prices for a particular day and you want to identify the best time to buy and sell a stock to maximize your profit. You can calculate the minimum difference of all possible stocks during the day to find the optimal buying and selling points using array concept.
INPUT FORMAT:
The first line contains the number of stocks during the day: n
The second line array representing the prices of a n stocks at different times during the day.
OUTPUT FORMAT:
Print the minimum difference in an array of stock prices
CONSTRAINTS:
1 <= n <= 105
1 <= stockPrices[i] <= n
TEST CASE 1:
Input:
5
3 -6  7 -7 0
Output: 
1
Explanation:
-6 and -7 give the smallest difference of all possible pairs, which is 1.
TEST CASE 2:
Input: 
5
1 6 9 12 4
Output:
2
Explanation:
6 and 4 give the smallest difference of all possible pairs, which is 2.


TEST CASE 3:
Input:
3
 1 9 12 
Output:
3
Explanation:
9 and 12 give the smallest difference of all possible pairs, which is 2.
ALGORITHM:
Declare and define the function `minDiffBruteForce` that takes an array `arr` and its size `n` as input.
Declare a variable `minDiff` and initialize it with the maximum possible value (`INT_MAX`).
Use nested loops to iterate over all pairs of elements in the array:
The outer loop runs from index 0 to index `n-2`.
The inner loop runs from the next index of the outer loop variable to index `n-1`.
Inside the inner loop:
Calculate the absolute difference between the elements at the current indices using the `abs()` function.
Update `minDiff` with the minimum of its current value and the calculated absolute difference.
After the loops, return the final value of `minDiff`.
In the `main()` function:
Declare an array `arr` and initialize it with values {3, -6, 7, -7, 0}.
Calculate the size of the array using the `sizeof` operator and divide it by the size of a single element `sizeof(arr[0])` to get the number of elements in the array.
Print the message "Minimum Difference is " followed by the result of `minDiffBruteForce(arr, n)` using the `printf` function.
SOURCE CODE:
#include <stdio.h>
#include <stdlib.h>

int minDiffBruteForce(int arr[], int n) {
  int minDiff = INT_MAX;

  for (int i = 0; i < n - 1; i++)
    for (int j = i + 1; j < n; j++) {
      int absDiff = abs(arr[i] - arr[j]);
      minDiff = (absDiff < minDiff) ? absDiff : minDiff;
    }

  return minDiff;
}
int main() 
{
    int n;
    printf("\nEnter number of stocks in a day:");
    scanf("%d",&n);
    int a[n];
    printf("\nEnter %d stock prices\n",n);
    for(int i = 0;i < n;i++)
    {
        scanf("%d",&a[i]);
    }
  //int arr[] = {3, -6, 7, -7, 0};
  //int n = sizeof(arr) / sizeof(arr[0]);

  printf("Minimum Difference is %d\n", minDiffBruteForce(a, n));

  return 0;
}
SAMPLE INPUT:
Enter the number of stock in a day: 5
Enter 5 stock prices
3 -6 7 -	7 0

SAMPLE OUTPUT:
Minimum Difference is 1

OUTPUT SCREENSHOTS: 






























RESULT:
Thus, the C program to program to find the minimum difference in stock prices using array concept is implemented and verified successfully. 

TASK NO: 1E
TASK NAME: Rotation
PROBLEM TITLE: Music Playlist Rotation
AIM:
To write a program to rotate the playlist by the given number of positions in a cyclic manner, ensuring that the songs are shifted and wrapped around appropriately.
PROBLEM DESCRIPTION:
You are building a music player application, and one of the features you want to implement is the ability to rotate the order of songs in a playlist. The rotation operation allows the user to change the order of songs, giving a different listening experience without having to manually reorder the songs.
Implement a function that takes a playlist (an array of song titles) and the number of positions to rotate the playlist. The function should rotate the playlist by the given number of positions in a cyclic manner, ensuring that the songs are shifted and wrapped around appropriately.
INPUT FORMAT:
The first line represents number of songs : length
The second line represents an array of song list : arr
The third line represents the number of steps to rotate the playlist : k
OUTPUT FORMAT:
Return the array of rotated playlist
CONSTRAINTS:
1 <= length <= 105
-231 <= arr[i] <= 231 - 1
0 <= k <= 105

TEST CASE 1:
Input:

10 20 30 40 50 60
2
Output: 
50 60 10 20 30 40

TEST CASE 2:
Input: 
23 45 67 98 14
3
Output:
67 98 14 23 45

TEST CASE 3:
Input:
1 2 3 4 5
2
Output:
4 5 1 2 3

ALGORITHM:
Declare an array
Initialize the array
Enter the index for circular rotation.
Perform circular operation.
Use two for loops and a temporary variable for the same.
Store the last element of the array in the temporary variable.
Using the second for loop shift element of the array by one.
The last element of the array will be added to the start of the array.
The resulting array is displayed at the end.
SOURCE CODE:
#include <stdio.h>
int main()
{
    //Declare the length of the array
    int length;
    printf("Enter the number of songs ");
    scanf("%d",&length);
    //Declare an array
    int arr[length];
    printf("Enter the playlist details ");
    for(int i=0;i<length;i++)    //Initialize array
    scanf("%d",&arr[i]);
    //n Enter the index for circular rotation i.e., the number of times the array should rotate
    int k;
    printf("Enter the number of steps");
    scanf("%d",&k);
    //Displays original array
    printf("Original array: \n");
    for (int i = 0; i < length; i++) {
        printf("%d ", arr[i]);
    }
    //Perform circular rotation for n times
    for(int i = 0; i < k; i++)
   {
           int j, temp;
           //Stores the last element of the array
            temp = arr[length-1];
            for(j = length-1; j > 0; j--)
            {
                   //Shift element of array by one
                    arr[j] = arr[j-1];
             }
            //Last element of the array will be added to the start of the array.
            arr[0] = temp;
    }
    printf("\n");
    //Display the array after rotation
    printf("Array after circular rotation: \n");
    for(int i = 0; i< length; i++){
        printf("%d ", arr[i]);
    }
    return 0;
}
SAMPLE INPUT:
Enter the number of songs 5
Enter the playlist details 10 20 30 40 50
Enter the number of steps2
SAMPLE OUTPUT:
Original array:
10 20 30 40 50
Array after circular rotation:
40 50 10 20 30
OUTPUT SCREENSHOTS: 


RESULT:
Thus, the C program to program to rotate the playlist by the given number of positions in a cyclic manner using array concept is implemented and verified successfully. 

TASK NO: 2 A
TASK NAME :  Linked List
PROBLEM TITLE:  Singly Linked List: Operations in Ascending Order
AIM:  
Design Develop and Implement the algorithm to perform the operation of sorting the elements in ascending order using Singly Linked List ADT.
PROBLEM DESCRIPTION:
Sort the nodes of the given singly linked list in ascending order
INPUT FORMAT:
The input line contains integers denoting elements of the given singly linked list.
 OUTPUT FORMAT:
Return the sorted list of elements that is provided in the input.
CONSTRAINTS:
0 <= n <= 10^5
TEST CASE 1:
24 67 34 89 12
TEST CASE 2:
98 23 102 56 34
TEST CASE 3:
21 67 19 56 90
ALGORITHM:
 1. Create a class Node which has two attributes: data and next. Next is a pointer            
            to the next node in the list.
 2. Create another class SortList which has two attributes: head and tail.
 3. addNode() will add a new node to the list:
Create a new node.
It first checks, whether the head is equal to null which means the list is empty.
If the list is empty, both head and tail will point to a newly added node.
If the list is not empty, the new node will be added to end of the list such that tail's next will point to a newly added node. This new node will become the new tail of the list.
 4. sortList() will sort the nodes of the list in ascending order.
Define a node current which will point to head.
Define another node index which will point to node next to current.
Compare data of current and index node. If current's data is greater than the index's data then, swap the data between them.
Current will point to current.next and index will point to index.next.
Continue this process until the entire list is sorted.

 5. display() will display the nodes present in the list:
Define a node current which will initially point to the head of the list.
Traverse through the list till current points to null.
Display each node by making current to point to node next to it in each iteration.
SOURCE CODE:
#include <stdio.h>
//Represent a node of the singly linked list
struct node{
    int data;
    struct node *next;
};
//Represent the head and tail of the singly linked list
struct node *head, *tail = NULL;
//addNode() will add a new node to the list
void addNode(int data) {
    //Create a new node
   struct node *newNode = (struct node*)malloc(sizeof(struct node));
    newNode->data = data;
   newNode->next = NULL;
  //Checks if the list is empty
  if(head == NULL) {
       //If list is empty, both head and tail will point to new node
    head = newNode;
   tail = newNode;
 }
    else {
       //newNode will be added after tail such that tail's next will point to newNode
       tail->next = newNode;
        //newNode will become new tail of the list
        tail = newNode;
    }
}
    //sortList() will sort nodes of the list in ascending order
    void sortList() {
        //Node current will point to head
        struct node *current = head, *index = NULL;
        int temp;
        if(head == NULL) {
            return;
        }
        else {
         while(current != NULL) {
              //Node index will point to node next to current
             index = current->next;
                while(index != NULL) {
                    //If current node's data is greater than index's node data, swap the data between them
         if(current->data > index->data) {
        temp = current->data;
             current->data = index->data;
                index->data = temp;
                    }
                    index = index->next;
                }
                current = current->next;
            }
        }
    }
//display() will display all the nodes present in the list
void display() {
    //Node current will point to head
    struct node *current = head;
    if(head == NULL) {
        printf("List is empty \n");
        return;
    }
    while(current != NULL) {
        //Prints each node by incrementing pointer
      printf("%d ", current->data);
        current = current->next;
    }
    printf("\n");
}
int main()
{
    //Add data to the list
    addNode(9);
    addNode(7);
    addNode(2);
    addNode(5);
    addNode(4);
    //Displaying original list
    printf("Original list: \n");
    display();
    //Sorting list
    sortList();
    //Displaying sorted list
    printf("Sorted list: \n");
    display();
    return 0;
}
SAMPLE INPUT:
Original List:
9 7 2 5 4
SAMPLE OUTPUT:
Sorted List:
2 4 5 7 9
OUTPUT SCREENSHOTS: 



RESULT: Thus, the C program has been executed to sort the elements in singly linked list.


TASK NO: 2 B
TASK NAME :  Doubly Linked List

PROBLEM TITLE:  Doubly Linked List: Get reversed in from the given order
AIM:  
Design, Develop and Implement the algorithm to perform the operation reversing the elements in Doubly Linked List ADT.
PROBLEM DESCRIPTION:
Given the pointer to the head node of a doubly linked list, reverse the order of the nodes in place. That is, change the next and prev pointers of the nodes so that the direction of the list is reversed. 

Note: The head node might be NULL to indicate that the list 
