Kth Max and Min Element of an Array in C
Here, in this page we will discuss the program to find Kth max and min element of an array in C programming language. We will first sort the array the array then print the required values.
Kth Max and Min Element of an Array in C
Algorithm :
Sort the entire array using merge sort.
After sorting, Kth maximum element will be at index arr_size-k.
And Kth minimum element is at k-1.
Time and Space Complexity :
Time Complexity : O(NLogN)
Space Complexity : O(N)
Code in C
//Program to find kth min and max element in C
#include <stdio.h>
#include <stdlib.h>
  
void merge(int arr[], int l, int m, int r)
{
    int i, j, k;
    int n1 = m - l + 1;
    int n2 = r - m;
  
    int L[n1], R[n2];
  
    for (i = 0; i < n1; i++)
        L[i] = arr[l + i];
    for (j = 0; j < n2; j++)
        R[j] = arr[m + 1 + j];
  
    i = 0; 
    j = 0; 
    k = l; 
    
    while (i < n1 && j < n2) {
        if (L[i] <= R[j]) {
            arr[k] = L[i];
            i++;
        }
        else {
            arr[k] = R[j];
            j++;
        }
        k++;
    }
  
    while (i < n1) {
        arr[k] = L[i];
        i++;
        k++;
    }
  
    while (j < n2) {
        arr[k] = R[j];
        j++;
        k++;
    }
}
  
void mergeSort(int arr[], int l, int r)
{
    if (l < r) {
        int m = l + (r - l) / 2;
  
        mergeSort(arr, l, m);
        mergeSort(arr, m + 1, r);
  
        merge(arr, l, m, r);
    }
}
 

int main()
{
    int arr[] = { 12, 11, 13, 5, 6, 7 };
    int arr_size = sizeof(arr) / sizeof(arr[0]);
    int k = 3;
    
    mergeSort(arr, 0, arr_size - 1);
  
    printf("K-th Maximum element : %d\n", arr[arr_size-k]);
    printf("K-th Minimum element : %d", arr[k-1]);
    
    return 0;
}
Output
K-th Maximum element : 11
K-th Minimum element : 7
