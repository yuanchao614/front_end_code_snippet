- 利用字符串可解构赋值(字符串默认转换成数组)实现对字符串首字母转大写，第二个参数为`true`则字符串首字母后的其他字符全部转小写，为`false`则不对首字母后的其它字符串做处理

```js
const capitalize = ([first, ...rest], lowerRest = false) =>
  first.toUpperCase() +
  (lowerRest ? rest.join('').toLowerCase() : rest.join(''));

```

example:

```js
capitalize('fooBar'); // 'FooBar'
capitalize('fooBar', true); // 'Foobar'
```
