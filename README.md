# front_end_code_snippet
Record my front end code snippet

- [Basic sort algorithms](#basic-sort-algorithms)
  - [Bunble sort](#bunble-sort)
  - [Selection sort](#selection-sort)
  - [Insert sort](#insert-sort)
  - [Merge sort](#merge-sort)
  
  
## Basic sort algorithms

### Bunble sort

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
