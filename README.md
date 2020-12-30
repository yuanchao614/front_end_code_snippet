# front_end_code_snippet
Record my front end code snippet

- [Basic sort algorithms](#basic-sort-algorithms)
  - [Bunble sort](#bunble-sort)
  - [Selection sort](#selection-sort)
  - [Insert sort](#insert-sort)
  - [Merge sort](#merge-sort)
  - [Quick sort](#quick-sort)
  
  
## Basic sort algorithms

### Bunble sort

![Algorithm Visualization](https://upload.wikimedia.org/wikipedia/commons/c/c8/Bubble-sort-example-300px.gif)

```javascript
    bunbleSort(originalArray) {
        if (originalArray.length <= 1) {
            return originalArray;
        }
        for (let i = 1; i < originalArray.length; i += 1) {
            for (let j = 0; j < originalArray.length - i; j += 1) {
                if (originalArray[j] > originalArray[j + 1]) {
                    [originalArray[j], originalArray[j + 1]] = [originalArray[j + 1], originalArray[j]];
                }
            }
        }
        return originalArray;
    }
```

### Selection sort

![Algorithm Visualization](https://upload.wikimedia.org/wikipedia/commons/9/94/Selection-Sort-Animation.gif)

```js
   selectionSort(originalArray) {
        if (originalArray.length <= 1) {
            return originalArray;
        }
        for (let i = 0; i < originalArray.length; i += 1) {
            let minIndex = i;
            for (let j = i + 1; j < originalArray.length; j += 1) {
                if (originalArray[minIndex] > originalArray[j]) {
                    minIndex = j;
                }
            }

            if (minIndex !== i) {
                [originalArray[i], originalArray[minIndex]] = [originalArray[minIndex], originalArray[i]];
            }
        }
        return originalArray;
    }
```

### Insert sort

![Algorithm Visualization](https://upload.wikimedia.org/wikipedia/commons/0/0f/Insertion-sort-example-300px.gif)

```js
  insertSort(originalArray) {
        if (originalArray.length <= 1) {
            return originalArray;
        }
        for (let i = 0; i < originalArray.length; i += 1) {
            let currentIndex = i;

            while (originalArray[currentIndex - 1] !== undefined && originalArray[currentIndex] < originalArray[currentIndex - 1]) {
                [
                    originalArray[currentIndex],
                    originalArray[currentIndex - 1]
                ] = [
                    originalArray[currentIndex - 1],
                    originalArray[currentIndex]
                ];
                currentIndex -= 1;
            }
        }
        return originalArray;
    }
```

### Merge sort

![Merge Sort](https://upload.wikimedia.org/wikipedia/commons/c/cc/Merge-sort-example-300px.gif)

```js
 mergeSort(originalArray) {
        if (originalArray.length <= 1) {
            return originalArray;
        }
        const middleIndex = Math.floor(originalArray.length / 2); // 向下取整
        const leftArray = originalArray.slice(0, middleIndex);
        const rightArray = originalArray.slice(middleIndex, originalArray.length);
        return this.mergeSortedArrays(leftArray, rightArray);
    }

    mergeSortedArrays(leftArray, rightArray) {
        const sortedArray = [];
        let leftIndex = 0;
        let rightIndex = 0;
        while (leftIndex < leftArray.length && rightIndex < rightArray.length) {
            let minElement = null;
            if (leftArray[leftIndex] < rightArray[rightIndex]) {
                minElement = leftArray[leftIndex];
                leftIndex += 1;
                sortedArray.push(minElement);
            } else {
                minElement = rightArray[rightIndex];
                rightIndex += 1;
                sortedArray.push(minElement);
            }
        }
        console.log(sortedArray.concat(leftArray.slice(leftIndex)).concat(rightArray.slice(rightIndex)));
        // 左边或右边都会有元素
        // 将其余元素连接到排序数组中
        return sortedArray
               .concat(leftArray.slice(leftIndex))
               .concat(rightArray.slice(rightIndex));
    }
```

### Quick sort

```js
sort(originalArray) {
        // Clone original array to prevent it from modification.
        const array = [...originalArray];
        // console.log(array);
        // If array has less than or equal to one elements then it is already sorted.
        if (array.length <= 1) {
          return array;
        }
        // Init left and right arrays.
        const leftArray = [];
        const rightArray = [];
        // Take the first element of array as a pivot.
        const pivotElement = array.shift();
        const centerArray = [pivotElement];
        // Split all array elements between left, center and right arrays.
        while (array.length) {
          const currentElement = array.shift();
          if (currentElement === pivotElement) {
            centerArray.push(currentElement);
          } else if (currentElement < pivotElement) {
            leftArray.push(currentElement);
          } else {
            rightArray.push(currentElement);
          }
        }
        // Sort left and right arrays.
        const leftArraySorted = this.sort(leftArray);
        const rightArraySorted = this.sort(rightArray);
        // Let's now join sorted left array with center array and with sorted right array.
        // console.log(leftArraySorted.concat(centerArray, rightArraySorted));
        return leftArraySorted.concat(centerArray, rightArraySorted);
      }
```
