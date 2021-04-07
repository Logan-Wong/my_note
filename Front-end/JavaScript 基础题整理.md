## JavaScript 基础题整理

### 1 非输出题

#### 1.1 关系型数组转换成树形结构对象

- 关系型数组

    ```javascript
    var obj = [
      { id: 3, parent: 2 },
      { id: 1, parent: null },
      { id: 2, parent: 1 }
    ]
    ```

- 期望结果

    ```javascript
    o = {
    	obj: {
    		id: 1,
    		parent: null,
    		child: {
    			id: 2,
    			parent: 1,
    			child: {
    				id: 3,
    				parent: 2
    			}
    		}
    	}
    }
    ```

编码实现：

```javascript
var arrToObj = function (arr) {
  // 先找出数组中属性 parent 值为 null 的对象，将该对象存入新对象中
  // 定义一个函数，实现通过给定 id 值找出其孩子并存入 curObj 的功能。

  let obj = {}
  for (item of arr) {
    if (item.parent == null) {
      obj.id = item.id
      obj.parent = item.parent
      break
    }
  }
  checkID(obj.id, obj, arr)
  return obj
}

var checkID = function (id, curObj, arr) {
  // 遍历数组
  for (item of arr) {
    if (item.parent == id) {
      if (!curObj.child) curObj.child = {}
      curObj.child.id = item.id
      curObj.child.parent = item.parent
      // 递归调用
      checkID(curObj.child.id, curObj.child, arr)
    }
  }
}
let array = [
  { id: 3, parent: 2 },
  { id: 1, parent: null },
  { id: 2, parent: 1 },
  { id: 5, parent: 3 }
]
console.log(arrToObj(array))
```

#### 1.2 实现一个方法对 URL 的查询参数（QueryString）解析。

例如 `/myurl?key0=&key1=val1&key2[]=0&key2[]=1page1` 解析返回

```javascript
{
  'key0': '',
  'key1': 'val1',
  'key2': ['0', '1']
}
```

代码实现：

```javascript
let queryData = function (queryStr) {
  let res = {}
  let arr = queryStr.split('?') // 只要问号后面的内容
  if (arr[1]) {
    // 分割 arr[1]
    arr[0] = arr[1]
  }
  arr[0] = arr[0].split('#')[0] // 去掉瞄点
  let tmpArr = arr[0].split('&')

  for (let key of tmpArr) {
    let curArr = key.split('=') // 用等号来分割
    // 先判断 curArr[0] 中包不包含中括号，有则处理为数组，没有则不予理会
    if (curArr[0].includes('[]')) {
      curArr[0] = curArr[0].split('[]')[0]
      // console.log(curArr[0]);
      if (!res[curArr[0]]) {
        res[curArr[0]] = []
      }
    }
    // 判断 curArr[1] 中是否为空
    if (curArr[1]) {
      if (res[curArr[0]] instanceof Array) {
        res[curArr[0]].push(curArr[1])
      } else {
        res[curArr[0]] = curArr[1]
      }
    } else {
      if (!(res[curArr[0]] instanceof Array)) {
        res[curArr[0]] = ''
      }
    }
  }
  return res
}
console.log(queryData('/myurl?key0=&key1=val1&key2[]=0&key2[]=1page1'))
```

### 2 输出题

```javascript
(function () {
  try {
    throw new Error()
  } catch (x) {
    var x = 1,
      y = 2
    console.log(x) // 预期输出 1
  }
  console.log(x) // 预期输出 undefined
  console.log(y) // 预期输出 2
})()
```

解释：catch 形成的块级作用域有点特殊，只对 catch 中的**参数**执行此特性，例如上例中的 x 和 y，x 的变量提升不到函数的作用域中，所以出现 undefined，而 y 由于不是 catch 的参数，所以可以提升到函数作用域。

---

```javascript
var length = 10
function fn() {
  console.log(this.length)
}

var obj = {
  length: 5,
  method: function (fn) {
    fn() // 预期输出 10
    arguments[0]() // 预期输出 2
  }
}

obj.method(fn, 1)
```

解释：arguments[0] 相当于调用了 fn 函数，此时的 this 指向 arguments 对象，那么 this.length 就相当于 arguments.length，代表参数个数，所以为 2。

---

```javascript
let a = {},
  b = '0',
  c = 0
a[b] = '珠峰'
a[c] = '培训'
console.log(a[b]) // 预期输出 培训
```

解释：对象中属性名不能重复，数字属性名和字符串属性名一样，所以会覆盖。

---

```javascript
let a = {},
	b = Symbol('1'),
  c = Symbol('1')
a[b] = '珠峰'
a[c] = '培训'
console.log(a[b])	// 预期输出 珠峰
```

解释：Symbol 创建的是唯一值！

---

```javascript
let a = {},
	b = { n: '1' },
  c = { m: '2' }
a[b] = '珠峰'
a[c] = '培训'
console.log(a[b])	// 预期输出 培训
```

解释：对象的属性值不是基本数据类型时，会转换为 [object object]，所以最后会转成一样的。

---

```javascript
var test = (function (i) {
  return function () {
    alert((i *= 2))
  }
})(2)
test(5) // 预期弹出（字符串） 4
```

解释：立即执行函数的返回结果赋值给 test 变量，但请注意，在调用 test 之前，立即执行函数会执行，但返回的结果是个函数，该函数没调用。最后调用 test，等于调用了立即执行函数返回的那个函数，此时传参 5，**但函数中没有形参接收**，alert 中的 i 用的是上一级作用域中的 i，也即是 2，所以最后结果为 4。『函数被执行时使用的作用域链(scope chain)是被定义时的作用域链，而不是执行时的作用域链！』

---

```javascript
var a = 0,
  b = 0
function A(a) {
  A = function (b) {
    alert(a + b++)
  }
  alert(a++)
}
A(1) // 预期弹出（字符串） 1
A(3) // 预期弹出（字符串） 5
```

解释：

---

```javascript
function Foo() {
  getName = function () {
    console.log(1)
  }
  return this
}
Foo.getName = function () {
  console.log(2)
}
Foo.prototype.getName = function () {
  console.log(3)
}
var getName = function () {
  console.log(4)
}
function getName() {
  console.log(5)
}
Foo.getName() // 1.预期输出 2
getName() // 2.预期输出 4
Foo().getName() // 3.预期输出 1
getName() // 4.预期输出 1
new Foo.getName() // 5.预期输出 2
new Foo().getName() // 6.预期输出 3
new new Foo().getName() // 7.预期输出 3
```

解释：

![image-20201019231921282](https://gitee.com/wlogan/pic-go-picture-bed/raw/master/images/20201019231930.png)

1. Foo 中有 getName() 方法，直接输出；
2. 根据变量提升的规则，最后全局作用域中的 getName() 中 4 覆盖 5，所以打印 4；
3. Foo() 返回 this，此时 this 指向 window，Foo() 函数得到执行，此时其中的 getName() 函数覆盖全局下的 getName()，所以输出 1；
4. 同上，输出 1；
5. new 运算符，构造函数不带括号的，应该从右往左执行。先执行 Foo.getName()，是输出为 2 的函数，然后再 new 这个函数，最后结果还是为 2；
6. new 运算符，构造函数带括号的，应该从左往右执行。先执行 new Foo()，得到实例对象，再执行实例对象的getName()，此时实例对象没有该方法，到原型上找，找到了，打印 3；
7. 先执行 new Foo().getName()，发现跟上一题一样，到最后返回 func->3，再 new func->3，结果返回 3。

---

```javascript
async function async1() {
  console.log('async1 start')
  await async2()
  console.log('async1 end')
}
async function async2() {
  console.log('async2')
}
console.log('script start')
setTimeout(function () {
  console.log('setTimeout')
}, 0)
async1()
new Promise(function (resolve) {
  console.log('promise1')
  resolve()
}).then(function () {
  console.log('promise2')
})
console.log('script end')

// 执行顺序如下：
// script start
// async1 start
// async2
// promise1
// script end
// async1 end
// promise2
// setTimeout
```

图解：

![image-20201020085659750](https://gitee.com/wlogan/pic-go-picture-bed/raw/master/images/20201020085659.png)

注意：代码执行到 await async2() 这里，会执行 async2() 函数，照常打印里面的语句，但要等 async2() 返回结果，才算执行完 await async2()，也即是到这里会阻塞，但是会执行 async2()。

---

问，a 等于什么值，才能使条件成立？

```javascript
if (a == 1 && a == 2 && a == 3) {
  console.log('条件成立')
}
```

1. 使用 toString()

    == 时，两边数据类型不一致会触发类型转换，观察发现，a 应该被转换为数字，系统自动调用 toString() 方法，我们重写该方法达到目的。

    ```javascript
    var a = {
    	i: 0,
    	toString() {
    		return ++this.i
    	}
    }
    if (a == 1 && a == 2 && a == 3) {
      console.log('条件成立')
    }
    ```

2. 用 Object.defineProperty() 进行数据劫持

    ```javascript
    var i = 0
    Object.defineProperty(window, 'a', {
      get() {
        return ++i
      }
    })
    if (a == 1 && a == 2 && a == 3) {
      console.log('条件成立')
    }
    ```

    ---

    