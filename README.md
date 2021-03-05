# front_end_code_snippet
Record my front end code snippet

- [Basic sort algorithms](#basic-sort-algorithms)
  - [Bunble sort](#bunble-sort)
  - [Selection sort](#selection-sort)
  - [Insert sort](#insert-sort)
  - [Merge sort](#merge-sort)
  - [Quick sort](#quick-sort)
  
- [CSS](#css)
  - [更改图片颜色](#更改图片颜色)
  
 - [Javascript](#javascript)
   - [Base64与ArrayBuffer的相互转换](#Base64与ArrayBuffer的相互转换)
   - [Blob转文件带下载](#Blob转文件带下载)
   - [Base64转Blob](#Base64转Blob)
   - [将数字四舍五入到固定的小数点](#将数字四舍五入到固定的小数点)
   - [判断给的日期是否为工作日](#判断给的日期是否为工作日)
   - [转换华氏/摄氏](#转换华氏/摄氏)
   - [根据路径获取对象的指定属性的值](#根据路径获取对象的指定属性的值)
   - [setTimeout与setInterval的相互实现](#setTimeout与setInterval的相互实现)
   - [根据对象数组的指定属性求平均数](#根据对象数组的指定属性求平均数)
   - [字符串单词首字母全大写](#字符串单词首字母全大写)
   - [统计数组中某个值出现的次数](#统计数组中某个值出现的次数)
   - [接收两个DOM元素对象参数，判断后者是否是前者的子元素](#接收两个DOM元素对象参数，判断后者是否是前者的子元素)
   - [按照给定的函数条件，查找第一个满足条件对象的键值](#按照给定的函数条件，查找第一个满足条件对象的键值)
   - [按照指定数组的深度，将嵌套数组进行展平](#按照指定数组的深度，将嵌套数组进行展平)
   - [返回两个日期之间相差多少天](#返回两个日期之间相差多少天)
   - [返回DOM元素是否包含指定的Class样式](#返回DOM元素是否包含指定的Class样式)
   - [隐藏指定的DOM元素](#隐藏指定的DOM元素)
   - [在给定的DOM节点后插入新的节点内容](#在给定的DOM节点后插入新的节点内容)
   - [在给定的DOM节点前插入新的节点内容](#在给定的DOM节点前插入新的节点内容)
   - [返回两个数组的交集](#返回两个数组的交集)
   - [JavaScript实现js/css链接的添加](#javaScript实现js/css链接的添加)
  
- [Angular](#angular)
  - [elementRef 为选择器添加class](#elementRef-为选择器添加class)
  - [TemplateRef 模板语法的使用](#TemplateRef-模板语法的使用)
  - [Angular项目中使用翻译](#Angular项目中使用翻译)
  
- [Vue](#vue)
  - [provide/inject](#provide/inject)
  
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

## CSS

### 更改图片颜色

```HTML
<p><strong>原始图标</strong></p>
<i class="icon icon-del"></i>
<p><strong>可以变色的图标</strong></p>
<i class="icon"><i class="icon icon-del"></i></i>
```

```CSS
.icon {
    display: inline-block;
    width: 20px; height: 20px;
    overflow: hidden;
}
.icon-del {
    background: url(delete.png) no-repeat center;
}
.icon > .icon {
    position: relative;
    left: -20px;
    border-right: 20px solid transparent;
    -webkit-filter: drop-shadow(20px 0);
    filter: drop-shadow(20px 0);
}
```
[参考链接](https://www.zhangxinxu.com/study/201606/png-icon-color-fill.html)

## JavaScript

### Base64与ArrayBuffer的相互转换

```js
function base64ToUint8Array(base64String) {
　　　　const padding = '='.repeat((4 - base64String.length % 4) % 4);
       const base64 = (base64String + padding)
                    .replace(/\-/g, '+')
                    .replace(/_/g, '/');

       const rawData = window.atob(base64);
       const outputArray = new Uint8Array(rawData.length);

       for (let i = 0; i < rawData.length; ++i) {
            outputArray[i] = rawData.charCodeAt(i);
       }
       return outputArray;
}


function arrayBufferToBase64(buffer) {
         let binary = '';
         const bytes = new Uint8Array(buffer);
         const len = bytes.byteLength;
         for (let i = 0; i < len; i++) {
               binary += String.fromCharCode(bytes[i]);
         }
         return window.btoa(binary);
}
```

### Blob转文件带下载

```ts
    /**
     * bold转文件带下载
     * @param _file_data || blob 文件流
     * @param _file_name 下载文件名称指定
     */
   blobDownloadFile(blob: Blob, fileName?: string) {
        const isBlob = blob instanceof Blob;
        if (!isBlob) {
            return;
        }
        const objectUrl = URL.createObjectURL(blob);
        const a = document.createElement('a');
        document.body.appendChild(a);
        a.setAttribute('style', 'display:none');
        a.setAttribute('href', objectUrl);
        a.setAttribute('download', fileName || `${Date.now()}.jpg`);
        a.click();
        document.body.removeChild(a);
        // 释放URL地址
        URL.revokeObjectURL(objectUrl);
    }
```

### Base64转Blob

```ts
  convertBase64UrlToBlob(base64: Base64): Blob {
        const parts = base64.dataUrl.split(';base64,');
        const contentType = parts[0].split(':')[1];
        const raw = window.atob(parts[1]);
        const rawLength = raw.length;
        const uInt8Array = new Uint8Array(rawLength);
        for (let i = 0; i < rawLength; i++) {
            uInt8Array[i] = raw.charCodeAt(i);
        }
        return new Blob([uInt8Array], { type: contentType });
    }
```

### 将数字四舍五入到固定的小数点

```js
const toFixed = (n, fixed) => ~~(Math.pow(10, fixed) * n) / Math.pow(10, fixed);
// Examples
toFixed(25.198726354, 1);       // 25.1
toFixed(25.198726354, 2);       // 25.19
toFixed(25.198726354, 3);       // 25.198
toFixed(25.198726354, 4);       // 25.1987
toFixed(25.198726354, 5);       // 25.19872
toFixed(25.198726354, 6);       // 25.198726
```

### 判断给的日期是否为工作日

> getDay() 方法根据本地时间，返回一个具体日期中一周的第几天，0 表示星期天。

```js
const isWeekday = (date) => date.getDay() % 6 !== 0;
console.log(isWeekday(new Date(2021, 0, 11)));
// Result: true (Monday)
console.log(isWeekday(new Date(2021, 0, 10)));
// Result: false (Sunday)
```

### 转换华氏/摄氏

```js

const celsiusToFahrenheit = (celsius) => celsius * 9/5 + 32;
const fahrenheitToCelsius = (fahrenheit) => (fahrenheit - 32) * 5/9;
// Examples
celsiusToFahrenheit(15);    // 59
celsiusToFahrenheit(0);     // 32
celsiusToFahrenheit(-20);   // -4
fahrenheitToCelsius(59);    // 15
fahrenheitToCelsius(32);    // 0
```

### 根据路径获取对象的指定属性的值

```ts
    getValueByPath(obj: any, paths = ''): unknown {
        let ret: unknown = obj;
        paths.split('.').map(path => {
            ret = ret[path];
        });
        return ret;
    }
```

### setTimeout与setInterval的相互实现

```js
// setinterval实现setTimeout

const mySetTimeout = (callback, time) => {
  const timer = setInterval(() => {
     clearInterval(timer)
     callback()
  }, time)
}

// setTimeout实现setInterval

 const mySetInterval = (callback, time) => {
        (function inner() {
            const timer = setTimeout(() => {
                callback();
                clearInterval(timer);
                inner();
            }, time);
        })();
    }

mySetTimeout(() => {console.log(123)}, 2000) // 2秒后输出123
mySetInterval(() => {console.log(123)}, 2000) // 每隔2秒输出一次123
```

### 根据对象数组的指定属性求平均数

```js
const averageBy = (arr, fn) =>
  arr.map(typeof fn === 'function' ? fn : val => val[fn]).reduce((acc, val) => acc + val, 0) /
  arr.length;
  
averageBy([{ n: 4 }, { n: 2 }, { n: 8 }, { n: 6 }], o => o.n); // 5
averageBy([{ n: 4 }, { n: 2 }, { n: 8 }, { n: 6 }], 'n'); // 5
```

### 字符串单词首字母全大写

```js
const capitalizeEveryWord = str => str.replace(/\b[a-z]/g, char => char.toUpperCase());
```

### 统计数组中某个值出现的次数

```js
const countOccurrences = (arr, val) => arr.reduce((a, v) => (v === val ? a + 1 : a), 0);
countOccurrences([1, 2, 1, 3, 1, 5, 1], 1) // 4
```

### 接收两个DOM元素对象参数，判断后者是否是前者的子元素。

```js

const elementContains = (parent, child) => parent !== child && parent.contains(child);

elementContains(document.querySelector('head'), document.querySelector('title')); // true
elementContains(document.querySelector('body'), document.querySelector('body')); // false
```

### 按照给定的函数条件，查找第一个满足条件对象的键值

```js
const findKey = (obj, fn) => Object.keys(obj).find(key => fn(obj[key], key, obj));

findKey(
  {
    barney: { age: 36, active: true },
    fred: { age: 40, active: false },
    pebbles: { age: 1, active: true }
  },
  o => o['active']
); // 'barney'
```

### 按照指定数组的深度，将嵌套数组进行展平

```js
// 默认深度为一层
const flatten = (arr, depth = 1) =>
  arr.reduce((a, v) => a.concat(depth > 1 && Array.isArray(v) ? flatten(v, depth - 1) : v), []);

flatten([1, [2], 3, 4]); // [1, 2, 3, 4]
flatten([1, [2, [3, [4, 5], 6], 7], 8], 2); // [1, 2, 3, [4, 5], 6, 7, 8]
```

### 返回两个日期之间相差多少天

```js

const getDaysDiffBetweenDates = (dateInitial, dateFinal) =>
  (dateFinal - dateInitial) / (1000 * 3600 * 24);
  
getDaysDiffBetweenDates(new Date('2019-01-13'), new Date('2019-01-15')); // 2
```

### 返回DOM元素是否包含指定的Class样式

```js

const hasClass = (el, className) => el.classList.contains(className);
hasClass(document.querySelector('p.special'), 'special'); // true
```

### 隐藏指定的DOM元素

```js

const hide = (...el) => [...el].forEach(e => (e.style.display = 'none'));

hide(document.querySelectorAll('img')); // Hides all <img> elements on the page
```

### 在给定的DOM节点后插入新的节点内容

```js
const insertAfter = (el, htmlString) => el.insertAdjacentHTML('afterend', htmlString);

insertAfter(document.getElementById('myId'), '<p>after</p>'); // <div id="myId">...</div> <p>after</p>
```

### 在给定的DOM节点前插入新的节点内容

```js
const insertBefore = (el, htmlString) => el.insertAdjacentHTML('beforebegin', htmlString);

insertBefore(document.getElementById('myId'), '<p>before</p>'); // <p>before</p> <div id="myId">...</div>
```

### 返回两个数组的交集

```js

const intersection = (a, b) => {
  const s = new Set(b);
  return a.filter(x => s.has(x));
};

intersection([1, 2, 3], [4, 3, 2]); // [2, 3]
```

### javaScript实现js/css链接的添加

```ts
const loadStyle = (url: string) => {
  const link = document.createElement('link')
  link.type = 'text/css'
  link.rel = 'stylesheet'
  link.href = url
  const head = document.getElementsByTagName('head')[0]
  head.appendChild(link)
}


const loadscript = (url: string) => {
  const script = document.createElement("script");
  script.type = "text/javacript";
  script.src = url;
  document.body.appendChild(script);
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

### Angular项目中使用翻译

* 1.app.module.ts 导入相应模块

```ts
import { HttpClientModule, HttpClient } from '@angular/common/http';
import { TranslateModule, TranslateLoader } from '@ngx-translate/core';
import { TranslateHttpLoader } from '@ngx-translate/http-loader';

// 导出加载json文件
export function createTranslateLoader(http: HttpClient) {
    return new TranslateHttpLoader(http, '/assets/i18n/', '.json');
}

    imports: [
        TranslateModule.forRoot({
            loader: {
                provide: TranslateLoader,
                useFactory: createTranslateLoader,
                deps: [HttpClient]
            }
        })
       ...
    ],
    declarations: [
        AppComponent,
       ...
    ],
    providers: [
    ],
    bootstrap: [AppComponent]
})
```

* app.components.ts中使用

```ts
import { TranslateService } from '@ngx-translate/core';

   constructor(
        private translate: TranslateService
    ) {
        // add support lang
        this.translate.addLangs(['en', 'ar']);

        // Sets the default language, usually used when a match cannot be made
        this.translate.setDefaultLang('en');
        
        //获取当前浏览器环境的语言比如en、 zh
        let browserLang = translate.getBrowserLang();
        translate.use(browserLang.match(/en|zh/) ? browserLang : 'en');
    }
```

* html或者components中使用

```thml
<div class="remove-multiple-tips">{{ 'EquipsDetail.DmsDetail.RemoveMultipleTips' | translate}}</div>
```

```ts
this.translate.get('EquipsDetail.DmsDetail.RemoveMultipleTips').subscrible(res => {
console.log(res)
})
```



## Vue/Vue3

### provide/inject

> provie/inject可实现多层组件嵌套的前提下跨组件通信，只需要在根级组件provide在后代的任何组件中inject便可获取根级组件的数据

```js
import { provide } from 'vue'
provie(key, value)

import { inject } from 'vue'
inject(key)
```

* 必须在setup()中使用
* 如果不传入响应式数据默认情况下数据不是响应式的

### Vue3 props参数使用interface

```ts
import {
  ...,
  PropType
} from "vue";
export interface UpdateUser {
    _id: string,
    userName: string,
    email: string,
    passWord: string,
    userType: string
    createdDate: Date,
    updatedDate: Date
}
....
  props: {
    viewUserVisible: {
      type: Boolean,
      default: false
    },
    action: {
      type: String,
      default: "create"
    },
    userData: {
      type: Object as PropType<UpdateUser>,
      required: true
    }
  }
```

## Rx.js

### rxjs通信与浏览器跨窗口通信

```ts
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
