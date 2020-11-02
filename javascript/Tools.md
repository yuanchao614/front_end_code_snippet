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
