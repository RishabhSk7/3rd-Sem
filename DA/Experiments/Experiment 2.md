![[Pasted image 20230907132734.png]]


NOTE: to plot the graphs, the C code will create a "\*.txt" as mentioned in the code. Run the following in terminal to show the plot:
```
$ Gnuplot
$gnuplot> plot "[filename].txt" w l smooth bezier
```
## Binary Search
Binary search is a search algorithm used to find a specific element in a sorted list or array by repeatedly dividing the search space in half.

Here's a brief explanation and its time complexities:

1. **Algorithm**:
    
    - Start with the entire sorted list.
    - Compare the middle element with the target value.
    - If the middle element is equal to the target, the search is complete.
    - If the middle element is greater than the target, search the left half.
    - If the middle element is less than the target, search the right half.
    - Repeat this process until the target is found or the search space becomes empty.

2. **Time Complexities**:
    
    - **Average Case**: O(log n)
    - **Worst Case**: O(log n)
    - **Best Case**: O(1)

Binary search is highly efficient for searching in large, sorted datasets because it reduces the search space by half with each comparison, resulting in logarithmic time complexity.

<b><u>Input</b> for the following program</u>: The program takes no input, instead has an array of pre-decided values `{10, 69, 500, 700, 1000, 1200, 1400, 1800, 2000, 5000, 7000}`. The program will sequentially take as many number of values randomly, and then sort them using the algorithm. The output is written to a text file. The values can be then plotted by:
```bash
$ gnuplot
> plot "binary-graph.txt" w l smooth bezier
```

```C
#include <stdio.h>

#include <stdlib.h>

#include <time.h>

  

int binary_search(int arr[], int size, int target)

{

int left = 0;

int right = size - 1;

  

while (left <= right)

{

int mid = (left + right) / 2;

if (arr[mid] == target)

{

return mid;

}

else if (arr[mid] < target)

{

left = mid + 1;

}

else

{

right = mid - 1;

}

}

  

return -1;

}

  

double measure_binary_search_time(int n)

{

int *sorted_array = (int *)malloc(sizeof(int) * n);

for (int i = 0; i < n; i++)

{

sorted_array[i] = i;

// printf("%d", i); //print number to get a better reading of time

}

  

int target = sorted_array[n-4];

clock();

clock_t start_time = clock();

int index = binary_search(sorted_array, n, target);

printf("%d\n", index);

clock_t end_time = clock();

  

free(sorted_array);

  

return ((double)(end_time - start_time) / CLOCKS_PER_SEC);

}

  

int main()

{

srand(time(NULL));

int n_values[] = {9, 1006407, 99065407, 410130815};

int num_values = sizeof(n_values) / sizeof(n_values[0]);

double time[4] = {};


for (int i = 0; i < num_values; i++)

{

int n = n_values[i];

double time_taken = measure_binary_search_time(n)*1000000;

time[i] = time_taken;

printf("Time taken for %d: %f ms\n", n, time_taken);

}

FILE *fp = NULL;

fp = fopen("binary-graph.txt", "w");

for (int i = 0;i<num_values;i++) {

fprintf(fp, "%d %f\n", n_values[i], time[i]);

printf("%d %f\n", n_values[i], time[i]);

}
return 0;
}
```

GRAPH(changes for each program run):
![[Pasted image 20230920225847.png|]]

## Linear Search
Linear search is a straightforward search algorithm that scans each element in a list or array to find a specific target element.

Here's a brief explanation and its time complexities:

1. **Algorithm**:
    
    - Start at the beginning of the list.
    - Compare each element with the target value sequentially.
    - If the current element is equal to the target, the search is complete.
    - If the end of the list is reached without finding the target, the search fails.

2. **Time Complexities**:
    
    - **Average Case**: O(n)
    - **Worst Case**: O(n)
    - **Best Case**: O(1)

Linear search has a time complexity of O(n) in the average and worst case scenarios because, in the worst case, you may have to examine every element in the list. The best-case time complexity is O(1) when the target is found in the first element, but this is a rare scenario. Linear search is most suitable for small lists or unsorted data but is not efficient for large datasets compared to algorithms like binary search for sorted data.

<b><u>Input</b> for the following program</u>: The program takes no input, instead has an array of pre-decided values `{10, 69, 500, 700, 1000, 1200, 1400, 1800, 2000, 5000, 7000}`. The program will sequentially take as many number of values randomly, and then sort them using the algorithm. The output is written to a text file. The values can be then plotted by:
```bash
$ gnuplot
> plot "linear-graph.txt" w l smooth bezier
```

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
{ int i;

for (i = 0; i < size; i++)

printf("%d ", arr[i]);

}

  

double measure_linear_search_time(int n)

{

int *sorted_array = (int *)malloc(sizeof(int) * n);

for (int i = 0; i < n; i++)

{

sorted_array[i] = i;

// printf("%d", i); //print number to get a better reading of time

}

  

int target = rand() % n;

  

clock_t start_time = clock();

int index = linearSearch(sorted_array, n, target);

clock_t end_time = clock();

  

free(sorted_array);

  

return ((double)(end_time - start_time) / CLOCKS_PER_SEC);

}

  

int main()

{

  

srand(time(NULL));

int n_values[] = {1006540, 10065407, 910065407, 1410065407};

int num_values = sizeof(n_values) / sizeof(n_values[0]);

double time[4] = {};

  

for (int i = 0; i < num_values; i++)

{

int n = n_values[i];

double time_taken = measure_linear_search_time(n) * 1000000;

time[i] = time_taken;

printf("Time taken for %d: %f ms\n", n, time_taken);

}

  

FILE *fp = NULL;

fp = fopen("linear-graph.txt", "w");

for (int i = 0; i < num_values; i++)

{

fprintf(fp, "%d %f\n", n_values[i], time[i]);

printf("%d %f\n", n_values[i], time[i]);

}

  

return 0;

}
```

GRAPH:
![[Pasted image 20230920203506.png]]

## Merge Sort
Merge sort is a divide-and-conquer sorting algorithm that divides an unsorted list or array into smaller sublists, sorts those sublists, and then merges them back together.

Here's a brief explanation and its time complexities:

1. **Algorithm**:
    
    - Divide the unsorted list into two halves until each sublist has one or zero elements (base case).
    - Sort each sublist.
    - Merge the sorted sublists back together to create a single, sorted list.
2. **Time Complexities**:
    
    - **Average Case**: O(n log n)
    - **Worst Case**: O(n log n)
    - **Best Case**: O(n log n)

Merge sort has a consistent time complexity of O(n log n) for all cases (average, worst, and best). It is known for its stability and is particularly useful for sorting linked lists and external sorting because it minimizes data movement. However, it may require additional memory for storing the temporary sublists during the merge process, depending on the implementation.

<b><u>Input</b> for the following program</u>: The program takes no input, instead has an array of pre-decided values `{10, 69, 500, 700, 1000, 1200, 1400, 1800, 2000, 5000, 7000}`. The program will sequentially take as many number of values randomly, and then sort them using the algorithm. The output is written to a text file. The values can be then plotted by:
```bash
$ gnuplot
> plot "merge-sort.txt" w l smooth bezier
```

```C
#include <stdio.h>
#include <stdlib.h>
#include <time.h>  

void merge(int arr[], int p, int q, int r)

{

int i, j, k;

int n1 = q - p + 1;

int n2 = r - q;

int L[n1], R[n2];

for (i = 0; i < n1; i++)

L[i] = arr[p + i];

for (j = 0; j < n2; j++)

R[j] = arr[q+p + j];

  

i = 0;

j = 0;

k = p;

while (i < n1 && j < n2)

{

if (L[i] <= R[j])

{

arr[k] = L[i];

i++;

}

else

{

arr[k] = R[j];

j++;

}

k++;

}

  

while (i < n1)

{

arr[k] = L[i];

i++;

k++;

}

  

while (j < n2)

{

arr[k] = R[j];

j++;

k++;

}

}

  

void mergeSort(int arr[], int l, int h)

{

if (l < h)

{

int m = l + (h - l) / 2;

  
  

mergeSort(arr, l, m);

mergeSort(arr, m + 1, h);

  

merge(arr, l, m, h);

}

}

  
  

double measure_merge_sort_time(int n) {

int *array = (int *)malloc(sizeof(int) * n);

for (int i = 0; i < n; i++)

{

array[i] = rand();

// printf("%d", i); //print number to get a better reading of time

}

  

clock_t start_time = clock();

mergeSort(array,0, n-1);

clock_t end_time = clock();

  

free(array);

  

return ((double)(end_time - start_time) / CLOCKS_PER_SEC);

}

  

int main()

{

srand(time(NULL));

int n_values[] = {10, 100, 1000, 10000};

int num_values = sizeof(n_values) / sizeof(n_values[0]);

double time[4];

  

for (int i = 0; i < num_values; i++)

{

int n = n_values[i];

double time_taken = measure_merge_sort_time(n) * 1000000;

time[i] = time_taken;

printf("Time taken for %d: %f ms\n", n, time_taken);

}

  

FILE *fp = NULL;

fp = fopen("merge-sort.txt", "w");

for (int i = 0; i < num_values; i++)

{

fprintf(fp, "%d %f\n", n_values[i], time[i]);

printf("%d %f\n", n_values[i], time[i]);

}

  

return 0;

}
```

GRAPH:
![[merge_sort.png]]

