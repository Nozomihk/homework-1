## 排序的算法过程
1.bubble sort eg.给六个数从小到大排序
```
#include <stdio.h>

int main() {
	int array[6];
	int temp;
	for(int i = 0; i < 6; ++ i)
	scanf("%d", &array[i]);
	for(int i = 0; i < 6; ++ i) {
		for(int j = 0; j < 5 - i; ++ j) {
			if(array[j] > array[j + 1]) {
				temp = array[j];
				array[j] = array[j + 1];
				array[j + 1] = temp;
			}
		}
	}
	for(int i = 0; i < 6; ++ i) {
		printf("%d ", array[i]);
	}
}
```
2.selection sort选择排序
```
function selectionSort(arr) {
    var len = arr.length;
    var minIndex, temp;
    for (var i = 0; i < len - 1; i++) {
        minIndex = i;
        for (var j = i + 1; j < len; j++) {
            if (arr[j] < arr[minIndex]) {  
                minIndex = j;                 
            }
        }
        temp = arr[i];
        arr[i] = arr[minIndex];
        arr[minIndex] = temp;
    }
    return arr;
} 
```
3.insertion sort插入排序
```
function insertionSort(arr) {
    var len = arr.length;
    var preIndex, current;
    for (var i = 1; i < len; i++) {
        preIndex = i - 1;
        current = arr[i];
        while (preIndex >= 0 && arr[preIndex] > current) {
            arr[preIndex + 1] = arr[preIndex];
            preIndex--;
        }
        arr[preIndex + 1] = current;
    }
    return arr;
}
```
