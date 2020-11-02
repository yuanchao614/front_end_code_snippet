工具类代码片段

- 判断初始值是否为所需类型，不是则返回备用值.

```js
factory(original: any, backup: any = ''): any {
        const srcType = this.typeOf(original);
        const desType = this.typeOf(backup);

        if (srcType === desType) {
            return original;
        } else {
            return backup;
        }
    }
```

- 生成随机颜色

```js
  getRandomColor() {
        return '#' + ('00000' + ((Math.random() * 0x1000000) << 0).toString(16)).slice(-6);
    }
```

- 添加`class`, `ele`为element`cls`为要添加的类名

```js
  addClass(ele, cls) {
        if (!this.hasClass(ele, cls)) {
            ele.className = ele.className === '' ? cls : ele.className + ' ' + cls;
        }
    }
```

- 判断类名是否存在

```js
   hasClass(ele, cls) {
        cls = cls || '';
        // 当cls没有参数时，返回false
        if (cls.replace(/\s/g, '').length === 0) {
            return false;
        }
        return new RegExp(' ' + cls + ' ').test(' ' + ele.className + ' ');
    }
```

 - 生成一个`img`标签
  
  ```js
    createImage(options: any = {}) {
        const img = document.createElement('img');
        if (options['src']) {
            img.src = options['src'];
        }
        return img;
    }
  ```
  
  - `base64`转`blob`

```js
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

- `blob`转文件并下载

```js
 downloadBlob(blob: Blob, fileName?: string) {
        // const blob = new Blob([_file_data], { type: 'application/vnd.openxmlformats-officedocument.spreadsheetml.sheet' });
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
    
    - 删除对象中指定属性`keys`为被删除属性名

```js
   isObjectDelKay(obj, keys) {
        if (!Array.isArray(obj)) {
            for (const i in obj) {
                if (obj.hasOwnProperty(i)) {
                    if (i === keys) {
                        delete obj[i];
                    }
                    if (Array.isArray(obj[i])) {
                        this.isObjectDelKay(obj[i], keys);
                    }
                }
            }
        } else {
            for (const i in obj) {
                if (obj.hasOwnProperty(i)) {
                    this.isObjectDelKay(obj[i], keys);
                }
            }
        }
        return obj;
    }
```
