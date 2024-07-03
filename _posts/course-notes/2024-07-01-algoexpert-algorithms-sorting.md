---
title: "Course Notes: AlgoExpert - Algorithm Questions - Sorting"
date: 2024-07-01T18:30:00+05:30
toc: true
toc_label: "Notes"
category: course-notes
---

*In this post, I summarize the various sorting algorithms discussed in __AlgoExpert - Algorithm Questions Course__ and implement them in Python.*

# Sorting Algorithms

## Bubble Sort

- In-place sort
- Last position of the list (or array) will have the largest number at the end of the first iteration
- We can optimize the code by reducing the loop by one. i.e. since the last position of the list has the largest number, we need not check it again, and we can only check till \\(n - 1 \\) elements.
- Space Complexity - \\(O (1) \\)
- Time Complexity (Worst and Average Case) - \\(O(N^2) \\)
- Time Complexity (Best Case = Already Sorted Array) -  \\(O(N) \\)

```python
def bubbleSort(array):
	isSorted = False
	counter = 0
	while not isSorted:
		isSorted = True
		for i in range(len(array) - 1 - counter):
			if array[i] > array[i+1]:
				swap(i, i+1, array)
				isSorted = False
		counter += 1
	return array
	
def swap(i, j, array):
	array[i], array[j] = array[j], array[i]
```

## Insertion Sort

- In-place sort
- Space Complexity - \\(O (1) \\)
- Time Complexity (Worst and Average Case) - \\(O(N^2) \\)
- Time Complexity (Best Case = Already Sorted Array) - \\(O(N) \\)

```python
def insertionSort(array):
	for i in range(1, len(array)):
		j = i
		while j > 0 and array[j] < array[j - 1]:
			swap(j, j - 1, array)
			j -= 1
	return array
			
def swap(i, j, array):
	array[i], array[j] = array[j], array[i]
```

## Selection Sort

- In-place sort
- Space Complexity - \\(O (1) \\)
- Time Complexity (All Cases) - \\(O(N^2) \\)

```python
def selectionSort(array):
	currentIdx = 0
	while currentIdx < len(array) - 1:
		smallestIdx = currentIdx
		for i in range(currentIdx + 1, len(array)):
			if array[smallestIdx] > array[i]:
				smallestIdx = i
		swap(currentIdx, smallestIdx, array)
		currentIdx += 1
	return array
		
def swap(i, j, array):
	array[i], array[j] = array[j], array[i]
```

## Three Number Sort

Given an array `nums` with `n` objects colored red, white, or blue, sort them **in-place** so that objects of the same color are adjacent, with the colors in the order red, white, and blue.

We will use the integers `0`, `1`, and `2` to represent the color red, white, and blue, respectively.

**Example 1:**

```
Input: nums = [2,0,2,1,1,0]
Output: [0,0,1,1,2,2]
```

**Example 2:**

```
Input: nums = [2,0,1]
Output: [0,1,2]
```

- Space Complexity - \\(O (1) \\)
- Time Complexity (All Cases) - \\(O(N) \\)

```python
def threeNumberSort(array, order):
	valueCounts = [0, 0, 0]
	
	for element in array:
		orderIdx = order.index(element)
		valueCounts[orderIdx] += 1
	
	for i in range(3):
		value = order[i]
		count = valueCounts[i]
		
		numElementsBefore = sum(valueCounts[:i])
		
		for n in range(count):
			currentIdx = numElementsBefore + n
			array[currentIdx] = value

	return array
```

```python
def threeNumberSort(array, order):
	firstValue = order[0]
	thirdValue = order[2]
	
	firstIdx = 0
	for idx in range(len(array)):
		if array[idx] == firstValue:
			swap(firstIdx, idx, array)
			firstIdx += 1
			
	thirdIdx = len(array) - 1
	for idx in range(len(array) - 1, -1, -1):
		if array[idx] == thirdValue:
			swap(thirdIdx, idx, array)
			thirdIdx -= 1
			
	return array

def swap(xi, j, array):
	array[i], array[j] = array[j], array[i]
```

```python
def threeNumberSort(array, order):
	firstValue = order[0]
	secondValue = order[1]
	
	# Keep track of the indices where the values are stored
	firstIdx, secondIdx, thirdIdx = 0, 0, len(array) - 1
	
	while secondIdx <= thirdIdx:
		value = array[secondIdx]
		
		if value == firstValue:
			swap(secondIdx, firstIdx, array)
			firstIdx += 1
			secondIdx += 1
		
		elif value == secondValue:
			secondIdx += 1
		
		else:
			swap(secondIdx, thirdIdx, array)
			thirdIdx -= 1
	
	return array
	
def swap(i, j, array):
	array[i], array[j] = array[j], array[i]
```

## Quick Sort

- Very famous, very fast, most commonly used in practice
- Time Complexity (Worst Case) - \\(O(N^2) \\)
- Time Complexity (Best Case) - \\(O(N \log N) \\)
- Time Complexity (Average Case) - \\(O(N \log N) \\)
- Space Complexity - \\(O(\log N) \\)

```python
def quickSort(array):
	quickSortHelper(array, 0, len(array) - 1)
	return array
	
def quickSortHelper(array, startIdx, endIdx):
	if startIdx >= endIdx:
		return
	
	# You could also pick random
	# pivotIdx = getRandomBetween(startIdx, endIdx)
	# But then you'll have to swap pivotIdx and startIdx
	# swap(pivotIdx, startIdx, array)
	pivotIdx = startIdx
	leftIdx = startIdx + 1
	rightIdx = endIdx
	
	while rightIdx >= leftIdx:
		if array[leftIdx] > array[pivotIdx] and array[rightIdx] < array[pivotIdx]:
			swap(leftIdx, rightIdx, array)
		if array[leftIdx] <= array[pivotIdx]:
			leftIdx += 1
		if array[rightIdx] >= array[pivotIdx]:
			rightIdx -= 1
	
	swap(pivotIdx, rightIdx, array)
	
	# Call on smaller sub-array
	leftSubarrayIsSmaller = (rightIdx - 1 - startIdx) < (endIdx - (rightIdx + 1))
	if leftSubarrayIsSmaller:
		quickSortHelper(array, startIdx, rightIdx - 1)
		quickSortHelper(array, rightIdx + 1, endIdx)
	else:
		quickSortHelper(array, rightIdx + 1, endIdx)
		quickSortHelper(array, startIdx, rightIdx - 1)
	
def swap(i, j, array):
	array[i], array[j] = array[j], array[i]
```

## Heap Sort

- Space Complexity - \\(O(1) \\)
- Time Complexity (All Cases) - \\(O (N \log N) \\)

```python
def heapSort(array):
	buildMaxHeap(array)
	
	for endIdx in reversed(range(1, len(array))):
		swap(0, endIdx, array)
		siftDown(0, endIdx - 1, array)
	
	return array
	
def buildMaxHeap(array):
	firstParentIdx = (len(array) - 1) // 2
	
	for currentIdx in reversed(range(firstParentIdx + 1)):
		siftDown(currentIdx, len(array) - 1, array)
		
def siftDown(currentIdx, endIdx, heap):
	childOneIdx = currentIdx * 2 + 1
	while childOneIdx <= endIdx:
		childTwoIdx = currentIdx * 2 + 2 if currentIdx * 2 + 2 <= endIdx else -1
		if childTwoIdx > -1 and heap[childTwoIdx] > heap[childOneIdx]:
			idxToSwap = childTwoIdx
		else:
			idxToSwap = childOneIdx
		if heap[idxToSwap] > heap[currentIdx]:
			swap(currentIdx, idxToSwap, heap)
			currentIdx = idxToSwap
			childOneIdx = currentIdx * 2 + 1
		else:
			return
	
def swap(i, j, array):
	array[i], array[j] = array[j], array[i]
```

## Radix Sort

- Time Complexity (All Cases) - \\(O (D \times (N + B)) \\)
    - \\(D \\) is the largest number of digits in an input
    - \\(N \\) is the number of elements in the input array
    - \\(B \\) is the base of the numbering system of the elements i.e. if we are working with decimal numbers \\(B = 10 \\), but if we are working with Hexadecimal numbers then \\(B = 16 \\)
- Space Complexity - \\(O(N + B) \\)
- This code will not work with negative numbers, the logic is different

```python
def radixSort(array):
	if len(array) == 0:
		return array
	
	maxNumber = max(array)
	
	digit = 0
	while maxNumber / (10 ** digit) > 0:
		countingSort(array, digit)
		digit += 1
	
	return array
	
def countingSort(array, digit):
	sortedArray = [0] * len(array)
	countArray = [0] * 10
	
	digitColumn = 10 ** digit
	for num in array:
		countIdx = (num // digitColumn) % 10
		countArray[countIdx] += 1
	
	for idx in range(1, 10):
		countArray[idx] += countArray[idx - 1]
		
	# Traverse in reverse to make it a 'stable' sort
	for idx in range(len(array) - 1, -1, -1):
		countIdx = (array[idx] // digitColumn) % 10
		countArray[countIdx] -= 1
		sortedIdx = countArray[countIdx]
		sortedArray[sortedIdx] = array[idx]
	
	for idx in range(len(array)):
		array[idx] = sortedArray[idx]
```

## Merge Sort

- Time Complexity - \\(O(N\log N) \\)
- Space Complexity (First Method) - \\(O(N \log N) \\)
- Space Complexity (Second Method) - \\(O(N) \\)

```python
# O(nlog(n)) time | O(nlog(n)) space

def mergeSort(array):
	if len(array) == 1:
		return array
	middleIdx = len(array) // 2
	leftHalf = array[:middleIdx]
	rightHalf = array[middleIdx:]
	return mergeSortedArrays(mergeSort(leftHalf), mergeSort(rightHalf))
	
def mergeSortedArrays(leftHalf, rightHalf):
	sortedArray = [None] * (len(leftHalf) + len(rightHalf))
	k = i = j = 0
	while i < len(leftHalf) and j < len(rightHalf):
		if leftHalf[i] <= rightHalf[j]:
			sortedArray[k] = leftHalf[i]
			i += 1
		else:
			sortedArray[k] = rightHalf[j]
			j += 1
		k += 1
	
	while i < len(leftHalf):
		sortedArray[k] = leftHalf[i]
		i += 1
		k += 1
	
	while j < len(rightHalf):
		sortedArray[k] = rightHalf[j]
		j += 1
		k += 1
	
	return sortedArray
```

```python
# O(nlog(n)) time | O(n) space

def mergeSort(array):
	if len(array) <= 1:
		return array
	auxiliaryArray = array[:]
	mergeSortHelper(array, 0, len(array) - 1, auxiliaryArray)
	return array

def mergeSortHelper(mainArray, startIdx, endIdx, auxiliaryArray):
	if startIdx == endIdx:
		return
	
	middleIdx = (startIdx + endIdx) // 2
	mergeSortHelper(auxiliaryArray, startIdx, middleIdx, mainArray)
	mergeSortHelper(auxiliaryArray, middleIdx + 1, endIdx, mainArray)
	doMerge(mainArray, startIdx, middleIdx, endIdx, auxiliaryArray)
	
def doMerge(mainArray, startIdx, middleIdx, endIdx, auxiliaryArray):
	k = startIdx
	i = startIdx
	j = middleIdx + 1
	while i <= middleIdx and j <= endIdx:
		if auxiliaryArray[i] <= auxiliaryArray[j]:
			mainArray[k] = auxiliaryArray[i]
			i += 1
		else:
			mainArray[k] = auxiliaryArray[j]
			j += 1
		k += 1
		
	while i <= middleIdx:
		mainArray[k] = auxiliaryArray[i]
		i += 1
		k += 1
	
	while j <= endIdx:
		mainArray[k] = auxiliaryArray[j]
		j += 1
		k += 1
```

## Count Inversions

**Inversion Count** **for an array indicates – how far (or close) the array is from being sorted. If the array is already sorted, then the inversion count is 0, but if the array is sorted in reverse order, the inversion count is the maximum.

Given an array `arr[]`. The task is to find the inversion count of `arr[]`. Where two elements `arr[i]` and `arr[j]` form an inversion if `a[i] > a[j]` and `i < j`.

**Examples**

- ***Input:*** `arr[] = {8, 4, 2, 1}`
    
    **Output:** 6
    
    **Explanation:** Given array has six inversions: (8, 4), (4, 2), (8, 2), (8, 1), (4, 1), (2, 1).
    
- ***Input:*** `arr[] = {1, 20, 6, 4, 5}`
    
    **Output:** 5
    
    **Explanation:** Given array has five inversions: (20, 6), (20, 4), (20, 5), (6, 4), (6, 5).
    
- Time Complexity (using Merge Sort) - \\(O(N \log N) \\)
- Space Complexity - \\(O(N) \\)

```python
def countInversions(array):
	return countSubArrayInversions(array, 0, len(array))
	
def countSubArrayInversions(array, start, end):
	if end - start <= 1:
		return 0
	
	middle = start + (end - start) // 2
	leftInversions = countSubArrayInversions(array, start, middle)
	rightInversions = countSubArrayInversions(array, middle, end)
	mergedArrayInversions = mergeSortAndCountInversions(array, start, middle, end)
	return leftInversions + rightInversions + mergedArrayInversions
	
def mergeSortAndCountInversions(array, start, middle, end):
	sortedArray = []
	left = start
	right = middle
	inversions = 0
	
	while left < middle and right < end:
		if array[left] <= array[right]:
			sortedArray.append(array[left])
			left += 1
		else:
			inversions += middle - left
			sortedArray.append(array[right])
			right += 1
	
	sortedArray += array[left:middle] + array[right:end]
	for idx, num in enumerate(sortedArray):
		array[start + idx] = num
		
	return inversions
```