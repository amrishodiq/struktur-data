# Implementasi algoritma MergeSort dengan Java


```
class MergeSort {
	// Merges two subarrays of array[]. 
    // First subarray is array[left .. middle] 
    // Second subarray is array[middle+1 .. right] 
	void merge(int array[], int left, int middle, int right) {
		// Find sizes of two subarrays to be merged
		int leftLength = middle - left + 1;
		int rightLength = right - middle;

		/* Create temp arrays */
		int L[] = new int[leftLength];
		int R[] = new int[rightLength];

		/* Copy data to temp arrays */
		for (int i = 0; i < leftLength; ++i)
			L[i] = array[left + i];
		for (int j = 0; j < rightLength; ++j)
			R[j] = array[middle + 1 + j];

		/* Merge the temp arrays */

		// Initial indexes of first and second subarrays
		int i = 0, j = 0;

		// Initial index of merged subarry array
		int k = left;
		while (i < leftLength && j < rightLength) {
			if (L[i] <= R[j]) {
				array[k] = L[i];
				i++;
			} else {
				array[k] = R[j];
				j++;
			}
			k++;
		}

		/* Copy remaining elements of L[] if any */
		while (i < leftLength) {
			array[k] = L[i];
			i++;
			k++;
		}

		/* Copy remaining elements of R[] if any */
		while (j < rightLength) {
			array[k] = R[j];
			j++;
			k++;
		}
	}

	// Main function that sorts array[left .. right] using
	// merge()
	void sort(int array[], int left, int right) {
		if (left < right) {
			// Find the middle point
			int middle = (left + right) / 2;

			// Sort first and second halves
			sort(array, left, middle);
			sort(array, middle + 1, right);

			// Merge the sorted halves
			merge(array, left, middle, right);
		}
	}

	/* A utility function to print array of size n */
	static void printArray(int array[]) {
		int n = array.length;
		for (int i = 0; i < n; ++i)
			System.out.print(array[i] + " ");
		System.out.println();
	}
}

public class Solution {

	public static void main(String[] args) {
		int array[] = {12, 11, 13, 5, 6, 7}; 
		
		MergeSort mergeSort = new MergeSort();
		System.out.println("Before sorted:");
		mergeSort.printArray(array);
		
		mergeSort.sort(array, 0, array.length - 1);
		
		System.out.println("After sorted:");
		mergeSort.printArray(array);
	}

}

```
