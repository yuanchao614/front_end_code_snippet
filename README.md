# front_end_code_snippet（我的前端代码片段）
Record my front end code snippet

- [Basic sort algorithms](#basic-sort-algorithms)
  - [Bunble sort](#bunble-sort)
  - [Selection sort](#selection-sort)
  - [Insert sort](#insert-sort)
  - [Merge sort](#merge-sort)
  - [Quick sort](#quick-sort)
  
- [CSS](#css)
  - [更改图片颜色](#更改图片颜色)
  - [css水平垂直居中](#css水平垂直居中)
  - [css画三角形](#css画三角形)
  
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
   - [JavaScript实现js/css链接的添加](#javaScript实现js或者css链接的添加)
   - [HTML5 file API加canvas实现图片前端JS压缩并上传](#HTML5fileAPI加canvas实现图片前端JS压缩并上传)
   - [准确判断数据类型](#准确判断数据类型)
   - [解析URL参数为对象](#解析URL参数为对象)
   - [防抖](#防抖)
   - [节流](#节流)
   - [数组去重](#数组去重)
   - [数组打平](#数组打平)
   - [深拷贝](#深拷贝)
   - [对象数组去重](#对象数组去重)
   - [阿拉伯数字转汉字](#阿拉伯数字转汉字)
   - [常用正则校验](#常用正则校验)
   - [取数组中最小值](#取数组中最小值)
  
- [Angular](#angular)
  - [elementRef 为选择器添加class](#elementRef-为选择器添加class)
  - [TemplateRef 模板语法的使用](#TemplateRef-模板语法的使用)
  - [Angular项目中使用翻译](#Angular项目中使用翻译)
  - [NGZORRO模态框实现拖拽](#NGZORRO模态框实现拖拽)
  
- [Http](#http)
  - [http缓存](#http缓存)
  
- [Vue](#vue)
  - [provide/inject](#provide/inject)
  - [Vue3反向代理解决跨域问题](#Vue3反向代理解决跨域问题)
  
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
                
                if (minIndex !== i) {
                   [originalArray[i], originalArray[minIndex]] = [originalArray[minIndex], originalArray[i]];
                }
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

### css水平垂直居中

* 已知宽高的情况
```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      .outer {
        position: relative;
        width: 400px;
        height: 600px;
        background: blue;
      }

      .inner {
        position: absolute;
        width: 200px;
        height: 300px;
        background: red;
        left: 50%;
        top: 50%;
        margin: -150px 0 0 -100px;
      }
    </style>
  </head>
  <body>
    <div class="outer">
      <div class="inner"></div>
    </div>
  </body>
</html>

```

* 宽高未知的内联元素如span

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      .outer {
        width: 400px;
        height: 600px;
        /* background: blue; */
        border: 1px solid red;
        background-color: transparent;
        position: relative;
      }

      .inner {
        position: absolute;
        background: red;
        left: 50%;
        top: 50%;
        transform: translate(-50%, -50%);
      }
    </style>
  </head>
  <body>
    <div class="outer">
      <span class="inner">我想居中显示</span>
    </div>
  </body>
</html>
```

* 绝对定位的 div 水平垂直居中

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      .outer {
        width: 400px;
        height: 600px;
        /* background: blue; */
        border: 1px solid red;
        background-color: transparent;
        position: relative;
      }

      .inner {
        position: absolute;
        background: red;
        left: 0;
        right: 0;
        bottom: 0;
        top: 0;
        width: 200px;
        height: 300px;
        margin: auto;
        border: 1px solid blue;
      }
    </style>
  </head>
  <body>
    <div class="outer">
      <div class="inner">我想居中显示</div>
    </div>
  </body>
</html>
```

* 图片使用<code>vertical-align: middle;</code>实现居中
* css3使用Flex居中

### css画三角形

```css
div { 
    width:0px; 
    height:0px; 
    border-top:10px solid red; 
    border-right:10px solid transparent; 
    border-bottom:10px solid transparent; 
    border-left:10px solid transparent; 
}

```

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

### javaScript实现js或者css链接的添加

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

### HTML5fileAPI加canvas实现图片前端JS压缩并上传

```html
<input id="file" type="file">
```

```js
var eleFile = document.querySelector('#file');

// 压缩图片需要的一些元素和对象
var reader = new FileReader(), img = new Image();

// 选择的文件对象
var file = null;

// 缩放图片需要的canvas
var canvas = document.createElement('canvas');
var context = canvas.getContext('2d');

// base64地址图片加载完毕后
img.onload = function () {
    // 图片原始尺寸
    var originWidth = this.width;
    var originHeight = this.height;
    // 最大尺寸限制
    var maxWidth = 400, maxHeight = 400;
    // 目标尺寸
    var targetWidth = originWidth, targetHeight = originHeight;
    // 图片尺寸超过400x400的限制
    if (originWidth > maxWidth || originHeight > maxHeight) {
        if (originWidth / originHeight > maxWidth / maxHeight) {
            // 更宽，按照宽度限定尺寸
            targetWidth = maxWidth;
            targetHeight = Math.round(maxWidth * (originHeight / originWidth));
        } else {
            targetHeight = maxHeight;
            targetWidth = Math.round(maxHeight * (originWidth / originHeight));
        }
    }
        
    // canvas对图片进行缩放
    canvas.width = targetWidth;
    canvas.height = targetHeight;
    // 清除画布
    context.clearRect(0, 0, targetWidth, targetHeight);
    // 图片压缩
    context.drawImage(img, 0, 0, targetWidth, targetHeight);
    // canvas转为blob并上传
    canvas.toBlob(function (blob) {
        // 图片ajax上传
        var xhr = new XMLHttpRequest();
        // 文件上传成功
        xhr.onreadystatechange = function() {
            if (xhr.status == 200) {
                // xhr.responseText就是返回的数据
            }
        };
        // 开始上传
        xhr.open("POST", 'upload.php', true);
        xhr.send(blob);    
    }, file.type || 'image/png');
};

// 文件base64化，以便获知图片原始尺寸
reader.onload = function(e) {
    img.src = e.target.result;
};
eleFile.addEventListener('change', function (event) {
    file = event.target.files[0];
    // 选择的文件是图片
    if (file.type.indexOf("image") == 0) {
        reader.readAsDataURL(file);    
    }
});

// https://www.zhangxinxu.com/study/201707/js-compress-image-before-upload.html
```

### 准确判断数据类型

typeof 可以正确识别：Undefined、Boolean、Number、String、Symbol、Function 等类型的数据，但是对于其他的都会认为是 object，比如 Null、Date 等，所以通过 typeof 来判断数据类型会不准确。但是可以使用 Object.prototype.toString 实现

```js
function typeOf(obj) {
    let res = Object.prototype.toString.call(obj).split(' ')[1]
    res = res.substring(0, res.length - 1).toLowerCase()
    return res
}
typeOf([])        // 'array'
typeOf({})        // 'object'
typeOf(new Date)  // 'date'

```

### 解析URL参数为对象

```js
function parseParam(url) {
    const paramsStr = /.+\?(.+)$/.exec(url)[1]; // 将 ? 后面的字符串取出来
    const paramsArr = paramsStr.split('&'); // 将字符串以 & 分割后存到数组中
    let paramsObj = {};
    // 将 params 存到对象中
    paramsArr.forEach(param => {
        if (/=/.test(param)) { // 处理有 value 的参数
            let [key, val] = param.split('='); // 分割 key 和 value
            val = decodeURIComponent(val); // 解码
            val = /^\d+$/.test(val) ? parseFloat(val) : val; // 判断是否转为数字
    
            if (paramsObj.hasOwnProperty(key)) { // 如果对象有 key，则添加一个值
                paramsObj[key] = [].concat(paramsObj[key], val);
            } else { // 如果对象没有这个 key，创建 key 并设置值
                paramsObj[key] = val;
            }
        } else { // 处理没有 value 的参数
            paramsObj[param] = true;
        }
    })
    
    return paramsObj;
}

![链接}(https://juejin.cn/post/6946022649768181774)
```

### 防抖

* 支持立即执行；
* 函数可能有返回值；
* 支持取消功能；

```js
function debounce(func, wait, immediate) {
    var timeout, result;
    
    var debounced = function () {
        var context = this;
        var args = arguments;
        
        if (timeout) clearTimeout(timeout);
        if (immediate) {
            // 如果已经执行过，不再执行
            var callNow = !timeout;
            timeout = setTimeout(function(){
                timeout = null;
            }, wait)
            if (callNow) result = func.apply(context, args)
        } else {
            timeout = setTimeout(function(){
                func.apply(context, args)
            }, wait);
        }
        return result;
    };

    debounced.cancel = function() {
        clearTimeout(timeout);
        timeout = null;
    };

    return debounced;
}

```

Example：

```js
var setUseAction = debounce(getUserAction, 10000, true);
// 使用防抖
node.onmousemove = setUseAction

// 取消防抖
setUseAction.cancel()
```

### 节流

支持取消节流；另外通过传入第三个参数，options.leading 来表示是否可以立即执行一次，opitons.trailing 表示结束调用的时候是否还要执行一次，默认都是 true。
注意设置的时候不能同时将 leading 或 trailing 设置为 false。

```js
function throttle(func, wait, options) {
    var timeout, context, args, result;
    var previous = 0;
    if (!options) options = {};

    var later = function() {
        previous = options.leading === false ? 0 : new Date().getTime();
        timeout = null;
        func.apply(context, args);
        if (!timeout) context = args = null;
    };

    var throttled = function() {
        var now = new Date().getTime();
        if (!previous && options.leading === false) previous = now;
        var remaining = wait - (now - previous);
        context = this;
        args = arguments;
        if (remaining <= 0 || remaining > wait) {
            if (timeout) {
                clearTimeout(timeout);
                timeout = null;
            }
            previous = now;
            func.apply(context, args);
            if (!timeout) context = args = null;
        } else if (!timeout && options.trailing !== false) {
            timeout = setTimeout(later, remaining);
        }
    };
    
    throttled.cancel = function() {
        clearTimeout(timeout);
        previous = 0;
        timeout = null;
    }
    return throttled;
}

```

### 数组去重

```js
// ES6
const unique = (arr) => Array.from(new Set(arr));

// 双重for循环

const unique = (arr) => {
        const array = [];
        for (let i = 0; i < arr.length; i++) {
            if (!array.includes(arr[i])) {
                arr.push(arr[i]);
            }
        }
    }
    
// includes方法

const unique = (arr) => {
        const array = [];
        for (let i = 0; i < arr.length; i++) {
            if (!array.includes(arr[i])) {
                arr.push(arr[i]);
            }
        }
    }
    
// filter + indexOf

const unique3 = (arr) => arr.filter((item, index, array) => array.indexOf(item) === index);
```

### 数组打平

```js
// ES6 flat方法

flat([1, 2, [3, 4]]) // [1, 2, 3, 4]

// ES6扩展运算符
const flater = (arr) => {
        while (arr.some(item => Array.isArray(item))) {
            arr = [].concat(...arr);
        }
        return arr;
    }
    
// ES6 reduce方法

flatten(arr) {
        return arr.reduce((result, item)=> {
            return result.concat(Array.isArray(item) ? flatten(item) : item);
        }, []);
    }
```

### 深拷贝

深拷贝开辟一个新的栈，两个对象属完成相同，但是对应两个不同的地址，修改一个对象的属性，不会改变另一个对象的属性

常见的深拷贝方式有：

* _.cloneDeep()

* jQuery.extend()

* JSON.stringify()

* 手写循环递归



```js

_.cloneDeep()
const _ = require('lodash');
const obj1 = {
    a: 1,
    b: { f: { g: 1 } },
    c: [1, 2, 3]
};
const obj2 = _.cloneDeep(obj1);
console.log(obj1.b.f === obj2.b.f);// false


jQuery.extend()
const $ = require('jquery');
const obj1 = {
    a: 1,
    b: { f: { g: 1 } },
    c: [1, 2, 3]
};
const obj2 = $.extend(true, {}, obj1);
console.log(obj1.b.f === obj2.b.f); // false


JSON.stringify()
const obj2=JSON.parse(JSON.stringify(obj1)); // 但是这种方式存在弊端，会忽略undefined、symbol和函数

const obj = {
    name: 'A',
    name1: undefined,
    name3: function() {},
    name4:  Symbol('A')
}
const obj2 = JSON.parse(JSON.stringify(obj));
console.log(obj2); // {name: "A"}


// 循环递归
function deepClone(obj, hash = new WeakMap()) {
  if (obj === null) return obj; // 如果是null或者undefined我就不进行拷贝操作
  if (obj instanceof Date) return new Date(obj);
  if (obj instanceof RegExp) return new RegExp(obj);
  // 可能是对象或者普通的值  如果是函数的话是不需要深拷贝
  if (typeof obj !== "object") return obj;
  // 是对象的话就要进行深拷贝
  if (hash.get(obj)) return hash.get(obj);
  let cloneObj = new obj.constructor();
  // 找到的是所属类原型上的constructor,而原型上的 constructor指向的是当前类本身
  hash.set(obj, cloneObj);
  for (let key in obj) {
    if (obj.hasOwnProperty(key)) {
      // 实现一个递归拷贝
      cloneObj[key] = deepClone(obj[key], hash);
    }
  }
  return cloneObj;
}

```

```js

  isClone(obj) {
        if (null == obj || 'object' !== typeof obj) {
            return obj;
        }
        if (obj instanceof Date) {
            const copy = new Date();
            copy.setTime(obj.getTime());
            return copy;
        }
        if (obj instanceof Array) {
            const copy = [];
            for (let i = 0, len = obj.length; i < len; ++i) {
                copy[i] = this.isClone(obj[i]);
            }
            return copy;
        }
        if (obj instanceof Object) {
            const copy = {};
            for (const attr in obj) {
                if (obj.hasOwnProperty(attr)) {
                    copy[attr] = this.isClone(obj[attr]);
                }
            }
            return copy;
        }
        throw new Error("Unable to copy obj! Its type isn't supported.");
    }
```


### 对象数组去重

```js
    /**
     * 对象数组去重
     * arr 原数组
     * property根据对象的某一属性去重
     */
    const unique = (arr, property) => {
      const res = new Map()
      return arr.filter((arr) => !res.has(arr[property]) && res.set(arr[property], 1))
    }
```

### 阿拉伯数字转汉字

```js
/**
 * 阿拉伯数字转汉字
 * @param {*} num 数字
 * @returns 阿拉伯数字对应汉字
 */
export const toChinesNum = (num) => {
  const changeNum = ['零', '一', '二', '三', '四', '五', '六', '七', '八', '九']
  const unit = ["", "十", "百", "千", "万"]
  num = parseInt(num)
  const getWan = (temp) => {
    const strArr = temp.toString().split("").reverse()
    let newNum = ""
    for (var i = 0; i < strArr.length; i++) {
      newNum = (i === 0 && strArr[i] === 0 ? "" : (i > 0 && strArr[i] === 0 && strArr[i - 1] === 0 ? "" : changeNum[strArr[i]] + (strArr[i] === 0 ? unit[0] : unit[i]))) + newNum
    }
    return newNum
  }
  const overWan = Math.floor(num / 10000)
  let noWan = num % 10000
  if (noWan.toString().length < 4) {
    noWan = "0" + noWan
  }
  return overWan ? getWan(overWan) + "万" + getWan(noWan) : getWan(num)
}

```

### 常用正则校验

```js
const PHONE_REG = /^1[3456789]\d{9}$/ // 手机号
const EMAIL_REG = /^\w+([-+.]\w+)*@\w+([-.]\w+)*\.\w+([-.]\w+)*$/

function isPhone (value) {
  return PHONE_REG.test(value)
}

function isEmail (value) {
  return EMAIL_REG.test(value)
}

```

### 去数组中最小值

```js
const getMinNum = arr => Math.min.apply(null, arr)
getMinNum([1, 3, 4, 6]) // 1
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

### NGZORRO模态框实现拖拽

directive.ts
```ts
import { Directive, ElementRef, HostListener, AfterViewInit, Renderer2 } from '@angular/core';

@Directive({
    selector: '[appDragModal]'
})
export class DragModalDirective implements AfterViewInit {
    canMove = false;
    modalX = 0;
    modalY = 0;
    mouseDownX = 0;
    mouseDownY = 0;
    distX = 0;
    distY = 0;
    constructor(private elementRef: ElementRef, private render: Renderer2) {
    }
    ngAfterViewInit() {
        const modalElement = this.getModalElement();
        const modalTitleElement = this.getModalTitleElment();
        console.log(modalElement);
        console.log(modalTitleElement);
        this.render.listen(modalTitleElement, 'mousedown', (event) => {
            this.mouseDownX = event.clientX;
            this.mouseDownY = event.clientY;
            this.modalX = modalElement.offsetLeft;
            this.modalY = modalElement.offsetTop;
            this.distX = event.clientX - modalElement.offsetLeft;
            this.distY = event.clientY - modalElement.offsetTop;
            this.render.setStyle(modalElement, 'position', 'absolute');
            this.render.setStyle(modalElement, 'top', `${this.modalY}px`);
            this.render.setStyle(modalElement, 'left', `${this.modalX}px`);
            this.canMove = true;
        });
        this.render.listen(modalTitleElement, 'mouseup', (event) => {
            this.canMove = false;
            this.render.setStyle(modalElement, 'cursor', `default`);
        });
        this.render.listen(this.elementRef.nativeElement, 'mousemove', (event) => {
            if (this.canMove) {
                this.render.setStyle(modalElement, 'cursor', `move`);
                let moveX = event.clientX - this.distX;
                let moveY = event.clientY - this.distY;
                const modalWidth = modalElement.offsetWidth;
                const modalHeight = modalElement.offsetHeight;
                const cw = document.documentElement.clientWidth;
                const cy = document.documentElement.clientHeight;
                if (moveY < 0) {
                    moveY = 0;
                } else if (moveY > cy - modalHeight) {
                    moveY = cy - modalHeight;
                }
                if (moveX < 0) {
                    moveX = 0;
                } else if (moveX > cw - modalWidth) {
                    moveX = cw - modalWidth;
                }
                this.render.setStyle(modalElement, 'top', `${moveY}px`);
                this.render.setStyle(modalElement, 'left', `${moveX}px`);
                this.render.setStyle(modalElement, 'cursor', `move`);
            }
        });
    }
    getModalElement() {
        return this.elementRef.nativeElement.querySelector('.ant-modal');
    }
    getModalTitleElment() {
        console.log(this.elementRef.nativeElement)
        return this.elementRef.nativeElement.querySelector('.ant-modal-content');
    }
}


// thml

```

componet.thml

```html

<nz-modal
        appDragModal
        id="addOrEdit"
        class="category-modal"
        [nzMaskClosable]="false"
        [nzWidth]="'20%'"
        [(nzVisible)]="addOrEditVisible"
        [nzTitle]="addOrEdit === 'create'? createCategory : editCategory"
        [nzFooter]="null"
        (nzOnCancel)="handleCancel()"
        [class.isrtl]="ss.lang === 'ar'"
>

....

</nz-modal>
```

## Http

### http缓存

[https://juejin.cn/post/6844903634002509832](https://juejin.cn/post/6844903634002509832)
* 强缓存
Exprise
* 弱缓存Last Modified
* Etag
* html不缓存解决强弱缓存的缺点

### 从浏览器输入URL到页面的呈现发生了什么

[https://juejin.cn/post/6844903878652067853](https://juejin.cn/post/6844903878652067853)



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

### Vue3反向代理解决跨域问题

```js
// vue.config.js
module.exports = {
  devServer: {
      proxy: {
          '/api': {
              target: 'http://localhost:3000',  //  重新映射到后端接口的接口地址 
              // port: 3000,
              ws: true,  // 是否启用websockets
              secure: false,
              changeOrigin: true, //开启代理：在本地会创建一个虚拟服务端，然后发送请求的数据，并同时接收请求的数据，这样服务端和服务端进行数据的交互就不会有跨域问题
              pathRewrite: {'^/api': '/'} // 去掉接口地址中的api字符串
          }
          }
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
