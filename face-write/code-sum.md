### 实现一个promise
```javascript
//极简的实现
//极简的实现
class Promise {
    callbacks = [];
    constructor(fn) {
        fn(this._resolve.bind(this));
    }
    then(onFulfilled) {
        this.callbacks.push(onFulfilled);
    }
    _resolve(value) {
        this.callbacks.forEach(fn => fn(value));
    }
}
//首先创建一个构造函数Promise
// Promise实例接受一个函数作为参数传入，该函数有两个参数resolve函数和reject函数，

class Promise {
    callbacks = [];
    state = 'pending';//增加状态
    res = null;//保存结果
    constructor(fn) {
        //1. 创建 Promise 实例时传入的函数会被赋予一个函数类型的参数resolve，
        fn(this._resolve.bind(this));
    }
    //收集异步操作成功后将要执行的方法，以供在调用resolve时执行。
    then(onFulfilled) {
        if (this.state === 'pending') {//在resolve之前，跟之前逻辑一样，添加到callbacks中
          this.callbacks.push(onFulfilled);
        } else {//在resolve之后，直接执行回调，返回结果了
          onFulfilled(this.res);
        }
        return this;//实现链式调用
    }
    //2. resolve函数接收一个参数res，代表异步操作返回的结果
         //在异步操作成功时将异步操作的结果作为参数传递出去
         //resolve(res)调用触发then方法第一个参数的回调函数，所以在此同时获取then的参数进行调用
    _resolve(res) {
      this.state = 'fulfilled';//改变状态
      this.res = res;//保存结果
      this.callbacks.forEach(fn => {
        fn(res);
      });
    }
}

//Promise应用
let p = new Promise(resolve => {
    setTimeout(() => {
        console.log('done');
        resolve('5秒');
    }, 5000);
}).then((tip) => {
    console.log(tip);
})
```


### CSS 不定宽高的垂直水平居中
```css
/*这个问题我在项目中经常遇到，期初常用的方法是transform + absolute
后来css3流行起来，flex弹性伸缩布局非常好用，
后来在知乎上看到一个方法也可以实现 display：table-cell，父要固定宽高*/

/*使wrapper中 唯一的 子元素居中*/

/*一：flex*/
.wrapper {
    width: 300px;
    height: 300px;
    
    display: flex;
    justify-content: center;
    align-items: center;
}

/*二：flex + margin*/
.wrapper {
    width: 300px;
    height: 300px;

    display: flex;
}
.wrapper .son {
    margin: auto;
}

/*三：transform + absolute*/
.wrapper {
    width: 300px;
    height: 300px;
    
    position: relative;
}
.wrapper .son {
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
}

/*四：absolute + 四个方向的值相等*/
.wrapper {
    width: 300px;
    height: 300px;
    position: relative;
}
.wrapper .son {
    width: 170px;
    height: 20px;
    margin: auto;
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
}
```


### 节流函数

```javascript
const throttle = (fn, delay = 500) => {
  let flag = true;
  return (...args) => {
    if (!flag) return;
    flag = false;
    setTimeout(() => {
      fn.apply(this, args);
      flag = true;
    }, delay);
  };
};
```


### 防抖函数

```javascript
const debounce = (fn, delay) => {
  let timer = null;
  return (...args) => {
    clearTimeout(timer);
    timer = setTimeout(() => {
      fn.apply(this, args);
    }, delay);
  };
};
```


### 实现Event(event bus)
```javascript
//Event进行初始化,包括Event的事件清单
class EventEmeitter {
  constructor() {
    this._events = this._events || new Map(); // 储存事件/回调键值对
  }
}
// 触发名为type的事件
EventEmeitter.prototype.emit = function(type, ...args) {
  let handler = this._events.get(type);// 从储存事件键值对的this._events中获取对应事件回调函数
  if (args.length > 0) {
    handler.apply(this, args);
  } else {
    handler.call(this);
  }
  return true;
};
// 监听名为type的事件
EventEmeitter.prototype.addListener = function(type, fn) {
  if (!this._events.get(type)) {// 将type事件以及对应的fn函数放入this._events中储存
    this._events.set(type, fn);
  }
};

// 实例化
const emitter = new EventEmeitter();
// 监听一个名为arson的事件对应一个回调函数
emitter.addListener('arson', man => {
  console.log(`expel ${man}`);
});
// 我们触发arson事件,发现回调成功执行
emitter.emit('arson', 'low-end'); // expel low-end
```


### 冒泡排序
```javascript
function bubbleSort(arr) {
    var len = arr.length;
    for (var i = 0; i < len; i++) {
        for (var j = 0; j < len - 1 - i; j++) {
            if (arr[j] > arr[j+1]) {
                var temp = arr[j+1];
                arr[j+1] = arr[j];
                arr[j] = temp;
            }
        }
    }
    return arr;
}
```



### new  
```javascript
 //首先是创建实例对象{}
  //this 变量引用该对象，同时还继承了构造函数的原型
  //其次属性和方法被加入到 this 引用的对象中
  //并且新创建的对象由 this 所引用，最后隐式的返回 this

function _new() {
  let target = {};
  let [constructor, ...args] = [...arguments];
  target.__proto__ = constructor.prototype;
  const res = constructor.apply(target, args);
  return typeof res === "object" ? res : target;
}
```


### call 
```javascript
Function.prototype.myCall = function() {
  let [targetThis, ...args] = [...arguments];
  if(!targetThis){
    targetThis = typeof window === 'undefined' ? global : window;
  }
  targetThis.func = this;
  let result = targetThis.func(...args);
  delete targetThis.func;
  return result;
};
```



### apply
```javascript
Function.prototype.myApply = function(targetThis, rest) {
  let result = null;
  if(!targetThis){
    targetThis = typeof window === 'undefined' ? global : window;
  }
  targetThis.func = this;
  if(!rest) {
    result = targetThis.func();
  }else {
    result = targetThis.func(...rest);
  }
  delete targetThis.func;
  return result;
};
```



### 实现instanceOf

```javascript
function instance_of(L, R) {
  //L 表示左表达式，R 表示右表达式
  var O = R.prototype; // 取 R 的显示原型
  L = L.__proto__; // 取 L 的隐式原型
  while (true) {
    if (L === null) return false;
    if (O === L)
      // 这里重点：当 O 严格等于 L 时，返回 true
      return true;
    L = L.__proto__;
  }
}
```



### 柯里化函数
```javascript
const curry = function (fn) {
    return function nest(...args) {
        // fn.length表示函数的形参个数
        if (args.length === fn.length) {
            // 当参数接收的数量达到了函数fn的形参个数，即所有参数已经都接收完毕则进行最终的调用
            return fn(...args);
        } else {
            // 参数还未完全接收完毕，递归返回judge，将新的参数传入
            return function (arg) {
                return nest(...args, arg);
            }
        }
    }
}
function addNum(a, b, c) {
    return a + b + c;
}

const addCurry = curry(addNum);

addCurry(1)(2)(3);// 6
```



### 请求函数封装，可设置请求次数，请求失败则继续请求

```javascript
function request(url, body, successCallback, errorCallback, maxCount = 3) {
      return fetch(url, body)
        .then(response => successCallback(response))
        .catch(err => {
            if (maxCount <= 0) return errorCallback('请求超时');
            return request(url, body, successCallback, errorCallback, --maxCount);
        });
  }
  // 调用
  request('https://some/path', { method: 'GET', headers: {} }, (response) => {
      console.log(response.json());
  }, (err) => console.error(err));
```


### 5秒过去了

```javascript
function wait(n) {
          return new Promise((resolve,reject) => {
            setTimeout(() => {
              resolve()
            }, 5000)
          })
        }
    
        wait(5).then(() => {
          console.log('5s过去了')
        });
```


### findMax

```javascript
function name(arr) {
    return Math.max.apply(null, arr);
  }
  console.log(name([1,2,34,2]))
```


### forEach

```javascript
 let forEach = function(arr, fn) {
    for(var i = 0; i < arr.length; i++) {
      fn.call(arr, arr[i], i);
    }
  };
  forEach([1,2,3], (item, index) => console.log(item,index))
  
  Array.prototype._forEach = function(fn) {
      for(var i = 0; i < this.length; i++) {
        fn.call(this, this[i], i);
      }
    };
    [1,2,3]._forEach((item, index) => console.log(item,index))
```



### 数组去重
```javascript
  // 利用ES6 Set，Array.from  是将一个类数组对象或者可遍历对象转换成数组。 (浅拷贝的数组实例)
  function unique1(arr) {
    return Array.from(new Set(arr));  // return [...new Set(arr)];
  }
  
  //利用for嵌套for，然后splice去重
  function unique2(arr) {
      for(let i = 0; i < arr.length; i++) {
        for(let j = i + 1; j < arr.length; j++) {
          if(arr[i] === arr[j]) {   //第一个等同于第二个，splice方法删除第二个
            arr.splice(j, 1);
            j--;
          }
        }
      }
      return arr;
    }
    
   //利用indexOf去重
   function unique3(arr) {
       let result = [];
       for(let i = 0; i < arr.length; i++) {
         if(result.indexOf(arr[i]) === -1) {
           result.push(arr[i]);
         }
       }
       return result;
     }
     
    //利用includes
    function unique4(arr) {
        let result = [];
        for(let i = 0; i < arr.length; i++) {
          if(!result.includes(arr[i])) { // includes 检测数组是否包含当前项
            result.push(arr[i]);
          }
        }
        return result;
      }
   
    //利用filter   
       // indexOf(规定需检索的字符串值,规定在字符串中开始检索的位置)
       // 这里利用了fromindex 每次查找都从数组的第0项开始 比较查找到的的索引与当前的索引 相等则返回true 不相等则返回false 
    function unique5(arr) {
      return arr.filter((item, index, arr) => arr.indexOf(item, 0) === index );
    }
```



### 字符串相邻去重
```javascript
    var str = 'abcdaaaaabcd';
    function fn(str) {
      var res = "";
      var len = str.length;
      for (var i = 0; i < len; i++) {
        if (str[0] === str[1]) {
          str = str.slice(1);
        } else {
          res = res + str[0];
          str = str.slice(1);
        }
      }
      return res;
    }
    console.log(fn(str));
```



### 扁平化 
```javascript
let arr = [2, 4, 5, [34, 2, [1, 2, 3, 4, 5], 45, [12, 34, 2, 2, 1], 2], 1];  
//要求输出：[1, 2, 3, 4, 5, 12, 34, 45]
function formatArray(arr) {
    // Array.from || [...Set]
    // return Array.from(new Set(arr.flat(Infinity))).sort((n1, n2) => n1 - n2);
    return [...new Set(arr.flat(Infinity))].sort((n1, n2) => n1 - n2);
  }
  console.log(formatArray(arr));// [1, 2, 3, 4, 5, 12, 34, 45]
  
  
  while (arr.some(item => Array.isArray(item))) {
    arr = [].concat(...arr);
  } 
```



### 数字千分位格式化

```javascript
function toThousands(num) {
     var num = (num || 0).toString(), result = '';
     while (num.length > 3) {
         result = ',' + num.slice(-3) + result;
         num = num.slice(0, num.length - 3);
     }
     if (num) { result = num + result; }
     return result;
}


var str="123598752";
var re=/(?=(?!(\b))(\d{3})+$)/g;
str=str.replace(re,",");
alert(str);
```