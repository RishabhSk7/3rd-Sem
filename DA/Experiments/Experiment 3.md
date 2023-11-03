![[Pasted image 20230921134306.png]]
![[Pasted image 20230921134331.png]]


**For Strassen's, printout the code as it is too long, printout the code in small form, and write the algorithm in the manual.**

## Quick Sort
Quick sort is a divide-and-conquer sorting algorithm that works by selecting a "pivot" element from an unsorted list and partitioning the other elements into two sublists, according to whether they are less than or greater than the pivot. The sublists are then recursively sorted.

Here's a brief explanation and its time complexities:

1. **Algorithm**:
   - Choose a pivot element from the list.
   - Partition the list into two sublists: elements less than the pivot and elements greater than the pivot.
   - Recursively apply the quick sort algorithm to each sublist.
   - Combine the sorted sublists along with the pivot to produce a fully sorted list.

2. **Time Complexities**:
   - **Average Case**: O(n log n)
   - **Worst Case**: O(n^2)
   - **Best Case**: O(n log n)

Quick sort has an average-case time complexity of O(n log n), making it very efficient for most practical scenarios. However, its worst-case time complexity is O(n^2) when the pivot selection is poor (e.g., always selecting the smallest or largest element). Quick sort is widely used due to its speed and in-place sorting (no extra memory needed), but it can be sensitive to the choice of pivot and may require additional measures to ensure good performance in all cases.

<b><u>Input</b> for the following program</u>: The program takes no input, instead has an array of pre-decided values `{10, 69, 500, 700, 1000, 1200, 1400, 1800, 2000, 5000, 7000}`. The program will sequentially take as many number of values randomly, and then sort them using the algorithm. The output is written to a text file. The values can be then plotted by:
```bash
$ gnuplot
> plot "quicksort.txt" w l smooth bezier
```

```C
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

void swap(int *a, int *b)
{
    int t = *a;
    *a = *b;
    *b = t;
}

int partition(int arr[], int low, int high) {
    int pivot = arr[high];
    int i = (low - 1);

    for (int j = low; j <= high - 1; j++)
    {

        if (arr[j] < pivot)
        {
            i++;
            swap(&arr[i], &arr[j]);
        }
    }
    swap(&arr[i + 1], &arr[high]);
    return (i + 1);
}

void quick_sort(int arr[], int low, int high)
{
    if (low < high)
    {
        int pi = partition(arr, low, high);

        quick_sort(arr, low, pi - 1);
        quick_sort(arr, pi + 1, high);
    }
}

double measure_quick_sort_time(int n)
{
    int *array = (int *)malloc(sizeof(int) * n);
    for (int i = 0; i < n; i++)
    {
        array[i] = rand();
        // printf("%d", i);            //print number to get a better reading of time
    }

    clock_t start_time = clock();
    quick_sort(array, 0, n - 1);
    clock_t end_time = clock();

    free(array);

    return ((double)(end_time - start_time) / CLOCKS_PER_SEC);
}

int main() {
    int n_values[] = {10, 69, 500, 700, 1000, 1200, 1400, 1800, 2000, 5000, 7000};

    int num_values = 11;
    double time[num_values];
    for (int i = 0; i < num_values; i++)
    {
        int n = n_values[i];
        double time_taken = measure_quick_sort_time(n) * 1000000;
        time[i] = time_taken;
        printf("Time taken for %d: %f ms\n", n, time_taken);
    }

    FILE *fp =fopen("quicksort.txt", "w");
    for (int i = 0; i < num_values; i++)
    {
        fprintf(fp, "%d %f\n", n_values[i], time[i]);
        printf("%d %f\n", n_values[i], time[i]);
    }

    return 0;
}
```

![[Pasted image 20231005144629.png]]

## Insertion Sort
Insertion sort is a simple sorting algorithm that builds the final sorted list one element at a time by repeatedly taking the next unsorted element and placing it in its correct position within the sorted part of the list.

Here's a brief explanation and its time complexities:

1. **Algorithm**:
   - Start with the second element (index 1) and consider it as the first "unsorted" element.
   - Compare the unsorted element with the elements in the sorted part and insert it into the correct position in the sorted part.
   - Repeat this process for each subsequent unsorted element until the entire list is sorted.

2. **Time Complexities**:
   - **Average Case**: O(n^2)
   - **Worst Case**: O(n^2)
   - **Best Case**: O(n)

Insertion sort has a time complexity of O(n^2) in the average and worst case scenarios because it involves nested loops for comparisons and swaps. However, it performs well for small lists or partially sorted data. The best-case time complexity is O(n) when the list is already nearly sorted because there are few or no comparisons needed.

<b><u>Input</b> for the following program</u>: The program takes no input, instead has an array of pre-decided values `{10, 69, 500, 700, 1000, 1200, 1400, 1800, 2000, 5000, 7000}`. The program will sequentially take as many number of values randomly, and then sort them using the algorithm. The output is written to a text file. The values can be then plotted by:
```bash
$ gnuplot
> plot "insertsort.txt" w l smooth bezier
```

```C

#include <time.h>
#include <stdio.h>
#include <stdlib.h>

void insertionSort(int arr[], int n)
{
    int i, key, j;
    for (i = 1; i < n; i++)
    {
        key = arr[i];
        j = i - 1;

        while (j >= 0 && arr[j] > key)
        {
            arr[j + 1] = arr[j];
            j = j - 1;
        }
        arr[j + 1] = key;
    }
}

double measure_insertion_sort_time(int n)
{
    int *array = (int *)malloc(sizeof(int) * n);
    for (int i = 0; i < n; i++)
    {
        array[i] = rand();
        // printf("%d", i);            //print number to get a better reading of time
    }

    clock_t start_time = clock();
    insertionSort(array, n);
    clock_t end_time = clock();

    free(array);

    return ((double)(end_time - start_time) / CLOCKS_PER_SEC);
}

int main()
{
    int n_values[] = {10, 69, 500, 700, 1000, 1200, 1400, 1800, 2000, 5000, 7000};

    int num_values = 11;
    double time[num_values];
    for (int i = 0; i < num_values; i++)
    {
        int n = n_values[i];
        double time_taken = measure_insertion_sort_time(n) * 1000000;
        time[i] = time_taken;
        printf("Time taken for %d: %f ms\n", n, time_taken);
    }

    FILE *fp = fopen("insertsort.txt", "w");
    for (int i = 0; i < num_values; i++)
    {
        fprintf(fp, "%d %f\n", n_values[i], time[i]);
        printf("%d %f\n", n_values[i], time[i]);
    }

    return 0;
}
```

![[Pasted image 20231005144743.png]]

## Strassen's Multiplication
Strassen's matrix multiplication is a divide-and-conquer algorithm that computes the product of two matrices using a set of recursive formulas that reduce the number of multiplications required.

Here's a brief explanation and its time complexities:

1. **Algorithm**:
    - Given two matrices, divide them into four smaller submatrices.
    - Recursively compute seven products of these submatrices using the formulas:
	    - - P1 = A11 * (B12 - B22)
		- P2 = (A11 + A12) * B22
		- P3 = (A21 + A22) * B11
		- P4 = A22 * (B21 - B11)
		- P5 = (A11 + A22) * (B11 + B22)
		- P6 = (A12 - A22) * (B21 + B22)
		- P7 = (A11 - A21) * (B11 + B12)
    - Combine these seven products to form the final product matrix. Final matrix is C if, C1, C2, C3, C4 are:
		- C11 = P5 + P4 - P2 + P6
		- C12 = P1 + P2
		- C21 = P3 + P4
		- C22 = P5 + P1 - P3 - P7

2. **Time Complexities**:
    
    - **Average Case**: O(n^log2(7)) ≈ O(n^2.807)
    - **Worst Case**: O(n^log2(7)) ≈ O(n^2.807)
    - **Best Case**: O(n^log2(7)) ≈ O(n^2.807)

Strassen's matrix multiplication has a lower time complexity than the standard matrix multiplication (O(n^3)) in the average case. However, its practical efficiency depends on factors like the matrix size and the particular implementation, and it may not always outperform the standard algorithm for small matrices due to the overhead of recursion and additional additions required. The time complexity of O(n^2.807) comes from the recursive nature of the algorithm, and it's often considered an improvement for large matrices.

```C
#include <stdio.h>
#include <math.h>
#include <time.h>

void add(int n, int A[n][n], int B[n][n], int C[n][n])
{
    for (int i = 0; i < n; i++)
        for (int j = 0; j < n; j++)
            C[i][j] = A[i][j] + B[i][j];
}

void subtract(int n, int A[n][n], int B[n][n], int C[n][n])
{
    for (int i = 0; i < n; i++)
        for (int j = 0; j < n; j++)
            C[i][j] = A[i][j] - B[i][j];
}

void multiply(int n, int A[n][n], int B[n][n], int C[n][n])
{
    for (int i = 0; i < n; i++)
    {
        for (int j = 0; j < n; j++)
        {
            C[i][j] = 0;
            for (int k = 0; k < n; k++)
            {
                C[i][j] += A[i][k] * B[k][j];
            }
        }
    }
}

void strassen(int n, int A[n][n], int B[n][n], int C[n][n])
{
    if (n == 1)
    {
        C[0][0] = A[0][0] * B[0][0];
        return;
    }

    int newSize = n / 2;
    int A11[newSize][newSize], A12[newSize][newSize], A21[newSize][newSize], A22[newSize][newSize];
    int B11[newSize][newSize], B12[newSize][newSize], B21[newSize][newSize], B22[newSize][newSize];
    int C11[newSize][newSize], C12[newSize][newSize], C21[newSize][newSize], C22[newSize][newSize];
    int P1[newSize][newSize], P2[newSize][newSize], P3[newSize][newSize], P4[newSize][newSize], P5[newSize][newSize], P6[newSize][newSize], P7[newSize][newSize];
    int temp1[newSize][newSize], temp2[newSize][newSize];

    for (int i = 0; i < newSize; i++)
    {
        for (int j = 0; j < newSize; j++)
        {
            A11[i][j] = A[i][j];
            A12[i][j] = A[i][j + newSize];
            A21[i][j] = A[i + newSize][j];
            A22[i][j] = A[i + newSize][j + newSize];

            B11[i][j] = B[i][j];
            B12[i][j] = B[i][j + newSize];
            B21[i][j] = B[i + newSize][j];
            B22[i][j] = B[i + newSize][j + newSize];
        }
    }

    add(newSize, A11, A22, temp1);
    add(newSize, B11, B22, temp2);
    strassen(newSize, temp1, temp2, P1);

    add(newSize, A21, A22, temp1);
    strassen(newSize, temp1, B11, P2);

    subtract(newSize, B12, B22, temp1);
    strassen(newSize, A11, temp1, P3);

    subtract(newSize, B21, B11, temp1);
    strassen(newSize, A22, temp1, P4);

    add(newSize, A11, A12, temp1);
    strassen(newSize, temp1, B22, P5);

    subtract(newSize, A21, A11, temp1);
    add(newSize, B11, B12, temp2);
    strassen(newSize, temp1, temp2, P6);

    subtract(newSize, A12, A22, temp1);
    add(newSize, B21, B22, temp2);
    strassen(newSize, temp1, temp2, P7);

    add(newSize, P3, P5, C12);
    add(newSize, P2, P4, C21);

    add(newSize, P1, P4, temp1);
    add(newSize, temp1, P7, temp2);
    subtract(newSize, temp2, P5, C11);

    add(newSize, P1, P3, temp1);
    add(newSize, temp1, P6, temp2);
    subtract(newSize, temp2, P2, C22);

    for (int i = 0; i < newSize; i++)
    {
        for (int j = 0; j < newSize; j++)
        {
            C[i][j] = C11[i][j];
            C[i][j + newSize] = C12[i][j];
            C[i + newSize][j] = C21[i][j];
            C[i + newSize][j + newSize] = C22[i][j];
        }
    }
}

int isPowerOfTwo(int n)
{
    return (n & (n - 1)) == 0;
}

int main()
{
    clock_t start, end;

    int n;

    printf("Enter the dimension for matrices (power of 2): ");
    scanf("%d", &n);

    if (!isPowerOfTwo(n))
    {
        printf("The dimension of the matrix should be a power of 2 to use Strassen Multiplication.\n");
        return 0;
    }

    int A[n][n], B[n][n], C[n][n], D[n][n];

    printf("Enter elements of matrix A:\n");
    for (int i = 0; i < n; i++)
    {
        for (int j = 0; j < n; j++)
        {
            // printf("Enter element at index [%d][%d]: ", i, j);
            scanf("%d", &A[i][j]);
        }
    }

    printf("Enter elements of matrix B:\n");
    for (int i = 0; i < n; i++)
    {
        for (int j = 0; j < n; j++)
        {
            // printf("Enter element at index [%d][%d]: ", i, j);
            scanf("%d", &B[i][j]);
        }
    }

    start = clock();
    strassen(n, A, B, C);
    end = clock();
    double time_taken_strassen = ((double)(end - start)) / CLOCKS_PER_SEC;

    printf("Resultant Matrix (Strassen's Multiplication):\n");
    for (int i = 0; i < n; i++)
    {
        for (int j = 0; j < n; j++)
        {
            printf("%d ", C[i][j]);
        }
        printf("\n");
    }
    printf("\nTime taken by Strassen's algorithm: %f seconds\n", time_taken_strassen);

    start = clock();
    multiply(n, A, B, D);
    end = clock();

    double time_taken_normal = ((double)(end - start)) / CLOCKS_PER_SEC;

    printf("\nResultant Matrix (Normal Multiplication):\n");
    for (int i = 0; i < n; i++)
    {
        for (int j = 0; j < n; j++)
        {
            printf("%d ", D[i][j]);
        }
        printf("\n");
    }
    printf("Time taken by Normal multiplication: %f seconds\n", time_taken_normal);

    return 0;
}
```