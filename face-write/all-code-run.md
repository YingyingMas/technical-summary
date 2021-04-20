# 代码执行结果

``` javascript

setTimeout(() => console.log(1));

new Promise((res, rej) => {
    console.log(2);
    res(3)
}).then(val => console.log(val))

console.log(4)
// 2 4 3 1





async function async1() {
    console.log(1);
    const result = await async2();
    console.log(3);
}

async function async2() {
    console.log(2);
}

Promise.resolve().then(() => {
    console.log(4);
    return new Promise((resolve) => {
        console.log(7);
        setTimeout(() => {
            console.log(8);
            resolve();
        })
    }).then(() => {
        console.log(9);
    })
});

setTimeout(() => {
    console.log(5);
});

async1();
console.log(6);
// 1 2 6 4 7 3 5 8 9






async function async1() {
    console.log(1);
    const result = await async2();
    console.log(3);
}

async function async2() {
    console.log(2);
}

async1();

Promise.resolve().then(() => {
    console.log(4);
});

setTimeout(() => {
    console.log(5);
});

console.log(6);
// 1 2 6 3 4 5







{
    let a = 1;
    var b = 2;
}
console.log(a); // ReferenceError: a is not defined.
console.log(b); // 2






for (let i = 0; i < 10; i++) {
    // ...
}
console.log(i); // ReferenceError: i is not defined






for (let i = 0; i < 10; i++) {
    // ...
}
console.log(i); // 10






var name = 'id';

function fn() {
    console.log(name);
    var name = 'jd.hk';
    console.log(name);
}
fn();
console.log(name)







var name = 'World!';
(function() {
    if (typeof name === 'undefined') {
        var name = 'jack';
        console.log('Goodbye' + name);
    } else {
        console.log('Hello' + name)
    }
})()
// Goodbyejack






var a = 10
function b() {
 a = 100
}
b()
console.log(a)
//考察函数中改变全局变量





var a = 10
function b() {
 a = 100
 return;
 function a() {}
}
b()
console.log(a)
//考察变量提升，变量提升，函数b中的函数a会提升到函数b内最前面，即a变量成了局部变量，函数b内再对a进行赋值都不会改变全局变量





var a = 10
if (true) {
 var a = 100
}
console.log(a)
//考察作用域,如果想输出10应该怎么改，可以把判断里的var改成let或const，let与const区别，暂时性死区




var name = 'win'
const obj = {
 name: 'obj',
 a: () => {
 console.log(this.name)
 }
}
const obj1 = {
 name: 'obj1'
}
obj.a.call(obj1)
//win，考察箭头函数this的指向



var resource = ['a.png', 'b.png', 'c.png', 'd.png', 'e.png', 'f.png', 'g.png', 'h.png'];
for (var i = 0; i < resource.length; i++) {
 var img = new Image();
 img.src = resource[i];
 img.onload = function () {
 console.log(i);
 };
}
//8个8，考察同步、异步、阻塞，答console.log执行时for循环已经执行完，i的取值是resource.length，
//问假如for循环特别慢，例如下载完成需要1s，但是for循需要10s，那么有没有可能console.log在for循环执行完毕之前执行--->不可能,因为onload是异步事件，JavaScript的for循环会阻塞onload事件的触发，最极端情况，如果for是个死循环，则onload永远也不会被触发




let arr = [];
for (let i = 0; i < 10; i++) {
 arr.push((finish) => {
 console.log(i);
 return function () {
 // do something
 finish();
 }
 });
}
var func = arr.reduce((pre, cur) => cur(pre));
func();
//函数式编程
```
