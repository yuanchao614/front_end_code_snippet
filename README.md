# front_end_code_snippet
Record my front end code snippet

- [Basic sort algorithms](#basic-sort-algorithms)
  - [Bunble sort](#bunble-sort)
  - [Selection sort](#selection-sort)
  - [Insert sort](#insert-sort)
  - [Merge sort](#merge-sort)
  - [Quick sort](#quick-sort)
  
- [Angular](#angular)
  - [elementRef 为选择器添加class](#add-calss-for-selector)
  - [TemplateRef 模板语法的使用](#TemplateRef)
  
- [Rx.js](#rx.js)
  - [rxjs通信与浏览器跨窗口通信](#rxjs通信与浏览器跨窗口通信)
  
  
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

## Angular

### 为选择器添加class

```ts
import { ElementRef } from '@angular/core';

@Component({
  selector: 'yc-test',
  .....
  })
  
export class YcTestComponent {
  constructor(private elementRef: ElementRef) {
    // TODO: move to host after View Engine deprecation
    this.elementRef.nativeElement.classList.add('my-test');
  }
}
```

### TemplateRef 模板语法的使用

```ts
import { ChangeDetectionStrategy, Component, ElementRef, Input, TemplateRef, ViewEncapsulation } from '@angular/core';

@Component({
  selector: 'nz-card-meta',
  exportAs: 'nzCardMeta',
  preserveWhitespaces: false,
  changeDetection: ChangeDetectionStrategy.OnPush,
  encapsulation: ViewEncapsulation.None,
  template: `
    <div class="ant-card-meta-avatar" *ngIf="nzAvatar">
      <ng-template [ngTemplateOutlet]="nzAvatar"></ng-template>
    </div>
    <div class="ant-card-meta-detail" *ngIf="nzTitle || nzDescription">
      <div class="ant-card-meta-title" *ngIf="nzTitle">
        <ng-container *nzStringTemplateOutlet="nzTitle">{{ nzTitle }}</ng-container>
      </div>
      <div class="ant-card-meta-description" *ngIf="nzDescription">
        <ng-container *nzStringTemplateOutlet="nzDescription">{{ nzDescription }}</ng-container>
      </div>
    </div>
  `
})
export class NzCardMetaComponent {
  @Input() nzTitle: string | TemplateRef<void> | null = null;
  @Input() nzDescription: string | TemplateRef<void> | null = null;
  @Input() nzAvatar: TemplateRef<void> | null = null;

  constructor(private elementRef: ElementRef) {
    // TODO: move to host after View Engine deprecation
    this.elementRef.nativeElement.classList.add('ant-card-meta');
  }
}
```

```html
    <nz-card nzHoverable style="width:240px" [nzCover]="coverTemplate">
      <nz-card-meta nzTitle="Europe Street beat" nzDescription="www.instagram.com"></nz-card-meta>
    </nz-card>
    <ng-template #coverTemplate>
      <img alt="example" src="https://os.alipayobjects.com/rmsportal/QBnOOoLaAfKPirc.png" />
    </ng-template>
```

## Rx.js

### rxjs通信与浏览器跨窗口通信

```ts
/**
 * @author: hhr
 * @time: 2018-04-19 10:48:58
 * @description: Observable·global
 */
import { Injectable } from '@angular/core';
import { Observable, BehaviorSubject, Subject } from 'rxjs';
import { MESSAGE_CHANNEL, SYSTEM_EVENT } from 'app/app.constants';

@Injectable()
export class BullySubjectService {
    protected subject$: Subject<Bully>;
    protected bSubject$: BehaviorSubject<Bully>;

    protected broadcast$Map = new Map();

    constructor() {
        if (!this.subject$) {
            this.subject$ = new Subject<Bully>();
        }

        if (!this.bSubject$) {
            this.bSubject$ = new BehaviorSubject<Bully>(null);
        }
    }

    /**
     * 观察者模式·接收  -- BS -- 用于先订阅后发
     */
    public getSubject(): Observable<Bully> {
        return this.subject$.asObservable();
    }

    /**
     * 观察者模式·发送  -- BS -- 用于先订阅后发
     * @param item Object
     */
    public setSubject(item: Bully) {
        this.subject$.next(item);
    }

    /**
     * 观察者模式·接收  -- BS -- 用于先发后订阅
     */
    public getBSubject(): Observable<Bully> {
        return this.bSubject$.asObservable();
    }

    /**
     * 观察者模式·发送  -- BS -- 用于先发后订阅
     * @param item Object
     */
    public setBSubject(item: Bully) {
        this.bSubject$.next(item);
    }

    /**
     * BS 重置
     */
    public resetBSubject(): void {
        this.bSubject$.next(null);
    }

    /**
     * 注册广播通讯频道,并接受消息
     * @param channel: MESSAGE_CHANNEL 频道
     */
    public registerBroadcastReceive(channel: MESSAGE_CHANNEL): Observable<Bully> {
        // const broadcast$ = new BroadcastChannel(channel);
        const key = channel;
        const broadcast$ = new BroadcastChannel(channel);

        this.broadcast$Map.set(key, broadcast$);
        broadcast$.addEventListener('message', (res: any) => {
            if (!res) {
                return;
            }
            const data = res['data'] as Bully;
            data.carrier = broadcast$;
            this.setSubject(data);
        });
        return this.getSubject();
    }

    /**
     * 注册广播通讯频道,并发送消息
     * @param channel: MESSAGE_CHANNEL 频道
     * @param item: Bully 要发送的消息
     */
    public registerBroadcastSend(channel: MESSAGE_CHANNEL, item: Bully): void {
        const broadcast$ = new BroadcastChannel(channel);
        broadcast$.postMessage(item);
    }

    /**
     * 关闭广播频道
     * @param channel: MESSAGE_CHANNEL 频道
     */
    public closeBroadcast(channel: MESSAGE_CHANNEL): void {
        const broadcast$ = this.broadcast$Map.get(channel);
        if (broadcast$) {
            broadcast$.close();
            this.broadcast$Map.delete(channel);
        }
    }
}

export interface Bully {
    type: SYSTEM_EVENT | string;
    data?: any;
    carrier?: any; // 信息载体
    fromGis?: boolean; // 消息是否来自gis
}

```
