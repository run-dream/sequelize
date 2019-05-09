1. validator-extra.js
通过引入并扩展[validator.js](https://www.npmjs.com/package/validator)提供了一系列的对字符串的校验的方法,并赋予了一些别名
代码解析
``` js
/**
 * @description 是否是正则表达式
 * @param {*} str
 * @param {*} pattern
 * @param {*} modifiers
 * @return
 */
regex(str, pattern, modifiers) {
    str += '';
    if (Object.prototype.toString.call(pattern).slice(8, -1) !== 'RegExp') {
        pattern = new RegExp(pattern, modifiers);
    }
    return str.match(pattern);
}
// 中间的 Object.prototype.toString.call(pattern).slice(8, -1) ！== ‘RegExp’ 
// 通过 Object.toString() 返回的 [object RegExp] 来判断pattern是否为 RegExp类型的对象
// 也可以用 !(pattern instanceof RegExp)

_.forEach(obj, (value, key)=>{
    //...
})
```
