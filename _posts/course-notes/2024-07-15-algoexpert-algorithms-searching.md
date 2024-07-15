---
title: "Course Notes: AlgoExpert - Searching Algorithms"
date: 2024-07-15T18:30:00+05:30
toc: true
toc_label: "Notes"
category: course-notes
---

*In this post, I summarize the various searching algorithms discussed in __AlgoExpert - Algorithm Questions Course__ and implement them in Python.*

[Code Repository](https://github.com/rugvedmhatre/algorithms-practice?tab=readme-ov-file#searching)

## Binary Search

- The array needs to be sorted to apply Binary Search
- Time Complexity - \\(O(\log N)\\)
- Space Complexity (iterative algorithm) - \\(O(1)\\)
- Space Complexity (recursive algorithm) - \\(O(\log N)\\)

```python
# O(log(n)) time | O(log(n)) space

def binarySearch(array, target):
	return binarySearchHelper(array, target, 0, len(array) - 1)
	
def binarySearchHelper(array, target, left, right):
	if left > right:
		return -1
	middle = (left + right) // 2
	potentialMatch = array[middle]
	if target == potentialMatch:
		return middle
	elif target < potentialMatch:
		return binarySearchHelper(array, target, left, middle - 1)
	else:
		return binarySearchHelper(array, target, middle + 1, right)
```

```python
# O(log(n)) time | O(1) space

def binarySearch(array, target):
	left = 0
	right = len(array) - 1
	
	while left <= right:
		middle = (left + right) // 2
		potentialMatch = array[middle]
		if target == potentialMatch:
			return middle
		elif target < potentialMatch:
			right = middle - 1
		else:
			left = middle + 1
	
	return -1
```

## Find Three Largest Numbers

- Time Complexity - \\(O(N)\\)
- Space Complexity - \\(O(1)\\)

```python
def findThreeLargestNumbers(array):
	threeLargest = [None, None, None]
	
	for num in array:
		updateLargest(threeLargest, num)
	
	return threeLargest
	
def updateLargest(threeLargest, num):
	if threeLargest[2] is None or num > threeLargest[2]:
		shiftAndUpdate(threeLargest, num, 2)
	elif threeLargest[1] is None or num > threeLargest[1]:
		shiftAndUpdate(threeLargest, num, 1)
	elif threeLargest[0] is None or num > threeLargest[0]:
		shiftAndUpdate(threeLargest, num, 0)
		
def shiftAndUpdate(array, num, idx):
	for i in range(idx + 1):
		if i == idx:
			array[i] = num
		else:
			array[i] = array[i + 1]
```

## Search in Sorted Matrix

- Each row of the matrix is sorted, and each column of the matrix is sorted.
- Time Complexity - \\(O(N+M)\\)
- Space Complexity - \\(O(1)\\)

```python
# O(n + m) time | O(1) space

def searchInSortedMatrix(matrix, target):
	row = 0
	col = len(matrix[0]) - 1
	while row < len(matrix) or col >= 0:
		if matrix[row][col] > target:
			col -= 1
		elif matrix[row][col] < target:
			row += 1
		else:
			return [row, col]
	return [-1, -1]
```

## Shifted Binary Search

- You begin with a sorted array, but it has been shifted by a certain value.
- Example: `array = [45, 61, 71, 72, 73, 0, 1, 21, 33, 45]`
- Your goal is to find the target value (for example: `33`) and return it’s index (in the above case the answer is `8`)
- Time Complexity - \\(O(\log N)\\)
- Space Complexity (iterative algorithm) - \\(O(1)\\)
- Space Complexity (recursive algorithm) - \\(O(\log N)\\)

```python
# O(log(n)) time | O(log(n)) space

def shiftedBinarySearch(array, target):
	return shiftedBinarySearchHelper(array, target, 0, len(array) - 1)
	
def shiftedBinarySearchHelper(array, target, left, right):
	if left > right:
		return -1
	
	middle = (left + right) // 2
	potentialMatch = array[middle]
	
	leftNum = array[left]
	rightNum = array[right]
	
	if target == potentialMatch:
		return middle
	elif leftNum <= potentialMatch:
		if target < potentialMatch and target >= leftNum:
			return shiftedBinarySearchHelper(array, target, left, middle - 1)
		else:
			return shiftedBinarySearchHelper(array, target, middle + 1, right)
	else:
		if target > potentialMatch and target <= rightNum:
			return shiftedBinarySearchHelper(array, target, middle + 1, right)
		else:
			return shiftedBinarySearchHelper(array, target, left, middle - 1)
```

```python
# O(log(n)) time | O(1) space

def shiftedBinarySearch(array, target):
	left = 0
	right = len(array) - 1
	
	while left <= right:
		middle = (left + right) // 2
		potentialMatch = array[middle]
	
		leftNum = array[left]
		rightNum = array[right]
	
		if target == potentialMatch:
			return middle
		elif leftNum <= potentialMatch:
			if target < potentialMatch and target >= leftNum:
				right = middle - 1
			else:
				left = middle + 1
		else:
			if target > potentialMatch and target <= rightNum:
				left = middle + 1
			else:
				right = middle - 1

	return -1
```

## Search for Range

- Your goal is to find the range of indices that contain our target number.
- Example: `array = [0, 1, 21, 33, 45, 45, 45, 45, 45, 45, 61, 71, 73]`
- Output: `[4, 9]`
- Time Complexity - \\(O(\log N)\\)
- Space Complexity (iterative algorithm) - \\(O(1)\\)
- Space Complexity (recursive algorithm) - \\(O(\log N)\\)

```python
# O(log(n)) time | O(log(n)) space

def searchForRange(array, target):
	finalRange = [-1, -1]
	alteredBinarySearch(array, target, 0, len(array) - 1, finalRange, goLeft=True)
	alteredBinarySearch(array, target, 0, len(array) - 1, finalRange, goLeft=False)
	return finalRange
	
def alteredBinarySearch(array, target, left, right, finalRange, goLeft):
	if left > right:
		return
	middle = (left + right) // 2
	
	if array[middle] < target:
		alteredBinarySearch(array, target, middle + 1, right, finalRange, goLeft)
	elif array[middle] > target:
		alteredBinarySearch(array, target, left, middle - 1, finalRange, goLeft)
	else:
		if goLeft:
			if middle == 0 or array[middle - 1] != target:
				finalRange[0] = middle
			else:
				alteredBinarySearch(array, target, left, middle - 1, finalRange, goLeft)
		else:
			if middle == len(array) - 1 or array[middle + 1] != target:
				finalRange[1] = middle
			else:
				alteredBinarySearch(array, target, middle + 1, right, finalRange, goLeft)
```

```python
# O(log(n)) time | O(1) space

def searchForRange(array, target):
	finalRange = [-1, -1]
	alteredBinarySearch(array, target, 0, len(array) - 1, finalRange, goLeft=True)
	alteredBinarySearch(array, target, 0, len(array) - 1, finalRange, goLeft=False)
	return finalRange
	
def alteredBinarySearch(array, target, left, right, finalRange, goLeft):
	while left <= right:
		middle = (left + right) // 2
		if array[middle] < target:
			left = middle + 1
		elif array[middle] > target:
			right = middle - 1
		else:
			if goLeft:
				if middle == 0 or array[middle - 1] != target:
					finalRange[0] = middle
					return
				else:
					right = middle - 1
			else:
				if middle == len(array) - 1 or array[middle + 1] != target:
					finalRange[1] = middle
					return
				else:
					left = middle + 1
```

## Quick Select

- Space Complexity - \\(O(1)\\)
- Time Complexity (Best and Average Case) - \\(O(N)\\)
- Time Complexity (Worst Case) - \\(O(N^2)\\)

```python
# O(n) time | O(1) space

def quickselect(array, k):
	position = k - 1
	return quickselecthelper(array, 0, len(array) - 1, position)
	 
def quickselecthelper(array, startIdx, endIdx, position):
	while True:
		if startIdx > endIdx:
			raise Exception("Your algorithm should never arrive here!")
		pivotIdx = startIdx
		leftIdx = startIdx + 1
		rightIdx = endIdx
		
		while leftIdx <= rightIdx:
			if array[leftIdx] > array[pivotIdx] and array[rightIdx] < array[pivotIdx]:
				swap(leftIdx, rightIdx, array)
			if array[leftIdx] <= array[pivotIdx]:
				leftIdx += 1
			if array[rightIdx] >= array[pivotIdx]:
				rightIdx -= 1
		
		swap(pivotIdx, rightIdx, array)
		
		if rightIdx == position:
			return array[rightIdx]
		elif rightIdx < position:
			startIdx = rightIdx + 1
		else:
			endIdx = rightIdx - 1
				
def swap(one, two, array):
	array[one], array[two] = array[two], array[one]
```

## Index Equals Value

- Goal is to find the first index where the index equals the value at that index.
- Time Complexity - \\(O(\log N)\\)
- Space Complexity (iterative algorithm) - \\(O(1)\\)
- Space Complexity (recursive algorithm) - \\(O(\log N)\\)

```python
# O(n) time | O(1) space

def indexEqualsValue(array):
	for index in range(len(array)):
		value = array[index]
		if index == value:
			return index
			
	return -1
```

```python
# O(log(n)) time | O(log(n)) space

def indexEqualsValue(array):
	return indexEqualsValueHelper(array, 0, len(array) - 1)
	
def indexEqualsValueHelper(array, leftIdx, rightIdx):
	if leftIdx > rightIdx:
		return -1
	
	middleIdx = (leftIdx + rightIdx) // 2
	middleVal = array[middleIdx]
	
	if middleVal < middleIdx:
		return indexEqualsValueHelper(array, middleIdx + 1, rightIdx)
	elif middleVal == middleIdx and middleIdx == 0:
		return middleIdx
	elif middleVal == middleIdx and array[middleIdx - 1] < middleIdx - 1:
		return middleIdx
	else:
		return indexEqualsValueHelper(array, leftIdx, middleIdx - 1)
```

```python
# O(log(n)) time | O(1) space

def indexEqualsValue(array):
	leftIdx = 0
	rightIdx = len(array) - 1 
	
	while leftIdx <= rightIdx:	
		middleIdx = (leftIdx + rightIdx) // 2
		middleVal = array[middleIdx]
		
		if middleVal < middleIdx:
			leftIdx = middleIdx + 1
		elif middleVal == middleIdx and middleIdx == 0:
			return middleIdx
		elif middleVal == middleIdx and array[middleIdx - 1] < middleIdx - 1:
			return middleIdx
		else:
			rightIdx = middleIdx - 1
			
	return -1
```