<h2>Brute Force Techniques</h2>
<ul>
<li>Sort a given set of elements, using bubble sort and selection sort, and hence find the time required to sort elements.
<li>Perform linear search and find the time required to search an element.
<li>Given a string called "TEXT"  with "n" number of characters and another string called "PATTERN" with "m" number of characters(m&lt;=n). Write a program which implenments brute force string matching to search for a given pattern in the text. If the pattern is present then find the position of first occurences of pattern in that text.
</ul>
## Bubble Sort

**Define:** Bubble Sort is a simple sorting algorithm that repeatedly steps through a list or array, compares adjacent elements, and swaps them if they are in the wrong order. The pass through the list is repeated until the list is sorted.

**Time Complexities:**

- Best Case: O(n)
- Average Case: O(n^2)
- Worst Case: O(n^2)

```C
// Optimized implementation of Bubble sort

#include <stdbool.h>

#include <stdio.h>

#include <stdlib.h>

#include <time.h>

  

void swap(int *xp, int *yp)

{

int temp = *xp;

*xp = *yp;

*yp = temp;

}

  

// An optimized version of Bubble Sort

void bubbleSort(int arr[], int n)

{

int i, j;

bool swapped;

for (i = 0; i < n - 1; i++)

{

swapped = false;

for (j = 0; j < n - i - 1; j++)

{

if (arr[j] > arr[j + 1])

{

swap(&arr[j], &arr[j + 1]);

swapped = true;

}

}

  

// If no two elements were swapped by inner loop,

// then break

if (swapped == false)

break;

}

}

  

// Driver program to test above functions

int main()

{

int size;

printf("Enter size of array to generate: ");

scanf("%d", &size);

int arr[size];

for (int i = 0; i < size; i++)

{

arr[i] = rand();

}

printf("Generated array.");

time_t start, end;

double cpu_time_used;

  

start = clock();

bubbleSort(arr, size);

end = clock();

cpu_time_used = ((double)(end - start)) / CLOCKS_PER_SEC;

  

printf("\nTime taken: %f units.\n", cpu_time_used);

return 0;

}

```


## Selection Sort

**Define:** Selection Sort is a sorting algorithm that divides the input list into two parts: the sorted part and the unsorted part. It repeatedly selects the smallest (or largest, depending on the desired order) element from the unsorted part and swaps it with the leftmost unsorted element, thus expanding the sorted part.

**Time Complexities:**

- Best Case: O(n^2)
- Average Case: O(n^2)
- Worst Case: O(n^2)

```C
#include <stdio.h>

#include <stdlib.h>

#include <time.h>

  

void swap(int *xp, int *yp)

{

int temp = *xp;

*xp = *yp;

*yp = temp;

}

  

void selectionSort(int arr[], int n)

{

int i, j, min_idx;

  

// One by one move boundary of unsorted subarray

for (i = 0; i < n - 1; i++)

{

// Find the minimum element in unsorted array

min_idx = i;

for (j = i + 1; j < n; j++)

if (arr[j] < arr[min_idx])

min_idx = j;

  

// Swap the found minimum element with the first element

if (min_idx != i)

swap(&arr[min_idx], &arr[i]);

}

}

  

// Driver program to test above functions

int main()

{

int size;

printf("Enter size of array to generate: ");

scanf("%d", &size);

int arr[size];

for (int i = 0; i < size; i++)

{

arr[i] = rand();

}

printf("Generated array.");


  

time_t start, end;

double cpu_time_used;

  

start = clock();

selectionSort(arr, size);

end = clock();

cpu_time_used = ((double)(end - start)) / CLOCKS_PER_SEC;

  

printf("\nTime taken: %f units.\n", cpu_time_used);

  

return 0;

}

```


## Linear Search

**Define:** Linear Search, also known as sequential search, is a simple search algorithm that checks each element in a list or array one by one until the target element is found or the entire list is searched.

**Time Complexities:**

- Best Case: O(1)
- Average Case: O(n)
- Worst Case: O(n)

```C
#include <stdio.h>

#include <time.h>

#include <stdlib.h>

  

// Linear Search

int linearSearch(int arr[], int n, int target)

{

for (int i = 0; i < n; i++)

{

if (arr[i] == target)

{

return i; // Element found, return its index

}

}

return -1; // Element not found

}

void printArray(int arr[], int size)

{

int i;

for (i = 0; i < size; i++)

printf("%d ", arr[i]);

}

  

int main()

{

  

int target;

  

int size;

printf("Enter size of array to generate: ");

scanf("%d", &size);

int arr[size];

for (int i = 0; i < size; i++)

{

arr[i] = rand();

}

printArray(arr, size);

printf("Generated array.\n");

printf("Enter element to search: ");

scanf("%d", &target);

  

time_t start, end;

double cpu_time_used;

  

start = clock();

int result = linearSearch(arr, size, target);

end = clock();

cpu_time_used = ((double)(end - start)) / CLOCKS_PER_SEC;

  

if (result != -1)

{

printf("Element %d found at index %d\n", target, result);

}

else

{

printf("Element %d not found in the array\n", target);

}

  

printf("Time taken for linear search: %f seconds\n", cpu_time_used);

  

return 0;

}
```



## Brute Force Pattern Search
```C
# include <stdio.h>

#include <stdlib.h>

#include <time.h>

#include <stdbool.h>

#include <string.h>

#include <time.h>

  

int main() {

  

/* Generate random string */

char chars[] = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ";

int nchars = strlen(chars);

int length;

printf("Length: ");

scanf("%d", &length);

int i;

char TEXT[length];

  
  
  

for (i = 0; i < length; i++)

{


}

  

printf("%s", TEXT);

  

char PATTERN[] = "ab";

int len_T=sizeof(TEXT)-1, len_P=sizeof(PATTERN)-1, check;

  

if(len_P>len_T) {

printf("Pattern is longer than text.");

return 0;

}

  

clock_t start, end;

double cpu_time_used;

start = clock();

for(int i =0;i<=len_T-len_P;i++) {

if (TEXT[i]==PATTERN[0]) {

for (int j = 0; j<len_P; j++) {

if (TEXT[i+j]==PATTERN[j]) {

check++;

}

}

if (check==len_P) {

printf("\nThe Pattern exists in the Text starting %d.\n", i);

end = clock();

cpu_time_used = ((double)(end - start)) / CLOCKS_PER_SEC;

printf("\n%lf", cpu_time_used);

return 0;

}

else {

check=0;

}

}

}

end = clock();

cpu_time_used = ((double)(end - start)) / CLOCKS_PER_SEC;

printf("\n%lf", cpu_time_used);

return 0;

}
```