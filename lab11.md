# 自动驾驶的伦理问题
"My assumption had been that we would think about how a car should decide between the lives of its passengers and the lives of pedestrians." 

"First, there is the fact that what is easy for humans is often hard for machines. Whether it is recognizing faces or riding bicycles, we are good at perception and mechanical tasks because evolution built these skills for us. That, however, makes these skills hard to teach or engineer. This is known as “Moravec’s Paradox.
Second, in a future where all cars are self-driving cars, small changes to driving behavior would make a big difference in the aggregate. Decisions made by engineers today, in other words, will determine not how one car drives but how all cars drive. Algorithms become policy.
Engineers teach computers how to recognize faces and objects using methods of machine learning. They can use machine learning also to help self-driving cars imitate how humans drive. But this isn’t a solution: It doesn’t solve the problem that wide-ranging decisions about safety and mobility are made by engineers.
Furthermore, self-driving cars shouldn’t drive like people. Humans aren’t actually very good drivers. And they drive in ethically troubling ways, deciding whether to yield at crosswalks, based on pedestrians’ age, race and income. For example, researchers in Portland have found that black pedestrians are passed by twice as many cars and had to wait a third longer than white pedestrians before they can cross."

"For myself, I began to question whether we need places called “crosswalks” at all? After all, self-driving cars can potentially make it safe to cross a road anywhere.
And it is not only crosswalks that become unnecessary. Traffic lights at intersections could be a thing of the past as well. Humans need traffic lights to make sure everyone gets to cross the intersection without crash and chaos. But self-driving cars could coordinate among themselves smoothly."

"With self-driving cars, societies can redesign their traffic systems. From the crosswalk to overall traffic design – it is mundane situations that raise really hard questions. Extreme situations are a distraction."
                                           ----Johannes Himmelreich
针对自动驾驶的伦理问题，Johannes Himmelreich认为虽然自动驾驶存在着伦理问题，但自动驾驶的安全性比人为驾驶要高，仍应采取自动驾驶。为了避免伦理问题，他认为应该对交通系统进行再设计。


## 排序的算法过程
1.bubble sort eg.给六个数从小到大排序

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

2.selection sort选择排序

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

3.insertion sort插入排序

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