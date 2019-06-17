1. model.js
model对应于数据库中的表模型。实例则表示一行数据。
- 引入的package：
a. [dottie](https://github.com/mickhansen/dottie.js/)：支持用.的方式来处理嵌套的对象，也可以使用lodash.get()
b. [bluebird](https://www.zhihu.com/question/25413141)：性能好的Promise库
- dataValues
用来储存数据数据的实际的值。
```js
  instance.field
  // is the same as
  instance.get('field')
  // is the same as
  instance.getDataValue('field')
```

sequelize会尝试定义默认的属性
- id 自增主键
- createdAt,updateAt,deletedAt timestamp 可以通过options。createdAt 来修改名字


scope:
用来定义常用的查询查询条件
```
const Model = sequelize.define('model', attributes, {
 defaultScope: {
  where: {
    username: 'dan'
  },
  limit: 12
 },
 scopes: {
  isALie: {
    where: {
      stuff: 'cake'
   }
 },
 complexFunction: function(email, accessLevel) {
  return {
    where: {
      email: {
        [Op.like]: email
      },
      access_level {
        [Op.gte]: accessLevel
     }
  }
}

 *
 * Model.findAll() // WHERE username = 'dan'
 * Model.findAll({ where: { age: { [Op.gt]: 12 } } }) // WHERE age > 12 AND username = 'dan'
 *
 * @example <caption>To invoke scope functions you can do</caption>
 * Model.scope({ method: ['complexFunction', 'dan@sequelize.com', 42]}).findAll()
 * // WHERE email like 'dan@sequelize.com%' AND access_level >= 42
```


- Tips
js 也有static method，标明应该用ClassName.staticMethod来调用

2. data-types.js

