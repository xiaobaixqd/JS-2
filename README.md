# 声明对象的两种语法
   1. let obj={'name':'frank','age':18}
   2. let obj=new Object({'name':'frank'})

## 细节：
   * 对象定义：无序的数据集合，键值对的集合
   * 键名是字符串，不是标识符，可以包含任何字符
   * 引号可省略，就算引号省略，键名还是字符串
   * 每个key都是对象的属性名（property），每个value都是对象的属性值
   * 不加[]的属性名会自动变成字符串，加了[]则会当做变量求值

# 如何删除对象的属性
   1. var obj={name;'frank',age:18} obj.name=undefined;这里删除的是属性值，name=undefined,age=18
   2. var obj2={name:'frank',age:18} delete obj2.name;把属性名和值都删了，只剩age:18
   3. 也可以这么写，delete obj['name']
   4. 'name' in obj 验证删了没有，不含属性名
   5. 'xxx' in obj && obj.name 含有属性名，但值为undefined

# 如何查看对象的属性
   * 查看自身属性：Object.keys(obj)
   * 查看自身+共有属性：console.dir(obj2)或obj2.__proto__
   * 判断一个属性是自身的还是共有的：obj.hasOwnProperty('toString')
   * 中括号语法：obj['key']，点语法：obj.key，坑人语法：obj[key] //变量key值一般不为'key'，优先使用中括号语法

# 如何修改或增加对象的属性
   1. 直接赋值：obj.key='xxx'或obj['key']='xxx'，但不能写成obj[key]='xxx'，不加引号key就是变量，不能确定值是什么
       * 批量赋值：Object.assign(obj,{age:18,gender:'man'})
   2. 修改或增加共有属性：无法通过自身修改或增加共有属性
       * let obj={},obj2={} //共有toString，obj.toString='xxx'只会修改自身属性，obj2.toString还是在原型上
       * Obj.prototype.toString='xxx'，一般来说不要修改原型，会引起很多问题
   3. 修改隐藏属性：Object.create
       * 例：
        ``` JavaScript
        var common ={'国籍':'中国',hairColor:'black'}
        var person=Object.create(common) // person的原型为common
        person.name='frank',person.age=18;
        person
        ```
   