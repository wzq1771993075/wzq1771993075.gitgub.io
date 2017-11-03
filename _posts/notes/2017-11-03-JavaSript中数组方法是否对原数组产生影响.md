---
layout: post
title: JavaSript中数组方法是否对原数组产生影响
category: 技术
tags: JavaScript

---

## 产生影响

### 栈方法

#### push

push()方法可以接收任意数量的参数，把它们逐个添加到数组末尾，并返回修改后数组的长度。

#### pop

pop()方法会删除数组最后一项，并将该项返回。

### 队列方法

#### shift

shift()方法会删除数组的第一项，并将该项返回。

#### unshift

unshift()方法可以在数组前端添加任意个项，并返回修改后数组的长度。

### 重排序方法

#### reverse

reverse()方法可以反转数组项的顺序。

    var arr = ['one', 'two', 'three'];
    arr.reverse(); 
    console.log(arr); // ['three', 'two', 'one']
    sort

#### sort 

sort()方法会对数组进行排序。
为了实现排序，sort()方法会调用每个数组项的toString()转型方法，然后比较得到的字符串。
sort()方法可以接收一个比较函数作为参数。该比较函数接收两个参数，如果第一个参数应该位于第二个参数之前，则返回一个负数；反之返回正数；若两个参数相等则返回0.

    // 默认排序
    var arr = ['B', 'C', 'A'];
    arr.sort();
    console.log(arr); // ['A', 'B', 'C']

    // 接收比较函数
    var values = [5, 1, 10, 0];
    values.sort(function(a, b) {
        return a-b;  // 升序
        // return b-a;  // 降序
    });
    console.log(values); // [0,1,5,10]

### 操作方法

#### splice

splice()方法可以从指定的索引开始删除若干元素，然后再从该位置添加若干元素。
splice()方法始终都会返回一个空数组，该数组中包含从原始数组中删除的项。

    var arr = ['Microsoft', 'Apple', 'Yahoo', 'AOL', 'Excite', 'Oracle'];
    var arrDel = arr.splice(2, 3, 'Google', 'Facebook'); // 从索引2开始删除3个元素,然后再添加两个元素
    console.log(arr);  // ['Microsoft', 'Apple', 'Google', 'Facebook', 'Oracle']
    console.log(arrDel);  // ['Yahoo', 'AOL', 'Excite']

## 不产生影响

### 转换方法

#### toString、toLocaleString

得到数组中每个值的字符串形式拼接而成的、一个以逗号分隔的字符串。
调用toString()时，会调用数组每一项的toString()方法。而调用toLocaleString()时，会调用数组每一项的toLocaleString()方法。

    var arr = ["red", "blue", "green"];
    var arrNew = arr.toString();
    console.log(arr);  // ["red", "blue", "green"]
    console.log(arrNew);  // red,blue,green
    valueOf

在《JavaScript高级教程》中，提到调用数组的valueOf()和toString()方法会返回相同的值。而实际上并非这样，valueOf()方法会返回数组的原始值。

    var arr = ["red", "blue", "green"];
    var arrNew = arr.valueOf();
    console.log(arr);  // ["red", "blue", "green"]
    console.log(arrNew);  // ["red", "blue", "green"]

#### join

join()方法使用指定的分隔符，将数组的每个元素连接起来，返回构建的字符串。
使用join()重现toString()方法的输出：arr.join(',')

    var arr = ["red", "blue", "green"];
    var arrNew = arr.join(',');
    console.log(arr);  // ["red", "blue", "green"]
    console.log(arrNew);  // red,blue,green

### 操作方法

#### concat

concat()方法可以基于当前数组中的所有项创建一个新数组。
具体来说，concat()方法会先创建当前数组的一个副本，然后将接收的参数添加到这个副本的末尾，最后返回新构建的数组。
如果没有给concat()方法传递参数，只是复制当前数组并返回副本。如果给concat()方法传递一个或多个数组，则会将数组的每一项都添加到结果数组中。

    var arr = ['A', 'B', 'C'];
    var arrNew = arr.concat(1, 2, [3, 4]);
    console.log(arr);  // ['A', 'B', 'C']
    console.log(arrNew);  // ['A', 'B', 'C', 1, 2, 3, 4]

#### slice

slice()方法可以基于当前数组中的一项或多项创建一个新数组。
slice()方法可以接收一或两个参数，即要返回项的起始和结束位置，但不包括结束位置。如果只有一个参数，slice()方法返回起始位置到数组末尾的所有项。如果参数为负数，则用数组长度+该参数来确定相应的位置。

    var arr = ['A', 'B', 'C', 'D', 'E', 'F', 'G'];
    arr.slice(0, 3); // 从索引0开始，到索引3结束，但不包括索引3: ['A', 'B', 'C']
    console.log(arr); // ["A", "B", "C", "D", "E", "F", "G"]

### 位置方法

ES5中定义了2中数组位置方法。每个方法接收两个参数：要查找的项、表示查找起点位置的索引。其中，第二个参数可选。

#### indexOf

indexOf()方法可以搜索一个指定元素的位置，返回该项在数组中的位置。如果没找到，则返回-1。indexOf()是从数组的开头开始向后查找。

    var arr = [10, 20, '30', 'xyz', 20];
    var pos = arr.indexOf(20);
    console.log(arr);  // [10, 20, "30", "xyz", 20]
    console.log(pos);  // 1

####lastIndexOf

lastIndexOf()方法与indexOf()方法类似，区别在于：lastIndexOf()从数组的末尾开始向前查找。

    var arr = [10, 20, '30', 'xyz', 20];
    var pos = arr.lastIndexOf(20);
    console.log(arr);  // [10, 20, "30", "xyz", 20]
    console.log(pos);  // 4

### 迭代方法

ES5中定义了5种数组迭代方法。每个方法都接收两个参数：要在每一项上运行的函数，和运行该函数的作用于对象。其中，第二个参数可选。传入这些方法中的函数会接收三个参数：数组项的值、该项的索引、数组对象本身。

#### forEach

对数组中的每一项运行给定函数。forEach()方法没有返回值。

    var arr = [1, 2, 3, 4, 5, 4, 3, 2, 1];
    var eachResult = arr.forEach(function(item, index, self) {
        return item += 2;
    });
    console.log(arr);  // [1, 2, 3, 4, 5, 4, 3, 2, 1]
    console.log(eachResult);  // undefined

#### map

对数组中的每一项运行给定函数。 map()方法返回每次函数调用的结果组成的数组。

    var arr = [1, 2, 3, 4, 5, 4, 3, 2, 1];
    var mapResult = arr.map(function(item, index, self) {
        return item * 2;
    });
    console.log(arr);  // [1, 2, 3, 4, 5, 4, 3, 2, 1]
    console.log(mapResult);  // [2, 4, 6, 8, 10, 8, 6, 4, 2]

#### filter

对数组中的每一项运行给定函数。filter()方法返回使给定函数返回true的项组成的数组。

    var arr = [1, 2, 3, 4, 5, 4, 3, 2, 1];
    var filterResult = arr.filter(function(item, index, self) {
        return item > 2;
    });
    console.log(arr);  // [1, 2, 3, 4, 5, 4, 3, 2, 1]
    console.log(filterResult);  // [3, 4, 5, 4, 3]

#### every

对数组中的每一项运行给定函数。every()方法会返回布尔值，如果给定函数对数组每一项都返回true，则返回true。

    var arr = [1, 2, 3, 4, 5, 4, 3, 2, 1];
    var everyResult = arr.every(function(item, index, self) {
        return item > 2;
    });
    console.log(arr);  // [1, 2, 3, 4, 5, 4, 3, 2, 1]
    console.log(everyResult);  // false

#### some

对数组中的每一项运行给定函数。some()方法会返回布尔值，如果给定函数对数组任意一项返回true，则返回true。

    var arr = [1, 2, 3, 4, 5, 4, 3, 2, 1];
    var someResult = arr.some(function(item, index, self) {
        return item > 2;
    });
    console.log(arr);  // [1, 2, 3, 4, 5, 4, 3, 2, 1]
    console.log(someResult);  // true

### 归并方法

ES5中定义了2种数组缩小方法。每个方法都接收两个参数：在每一项上调用的函数、作为缩小基础的初始值。其中，第二个参数可选。传入这些方法中的函数会接收四个参数：前一个值、当前值、项的索引、数组对象。

#### reduce

reduce()方法会迭代数组中的所有项，然后构建一个最终返回值。reduce()方法从数组的第一项开始，逐个遍历到最后。

    var arr = [1, 2, 3, 4, 5];
    var reduceResult = arr.reduce(function(prev, cur, index, self) {
        return prev + cur;
    });
    console.log(arr);  // [1, 2, 3, 4, 5]
    console.log(reduceResult);  // 15

#### reduceRight

reduceRight()方法与reduce()方法类似，区别在于：reduceRight()从数组的最后一项开始，向前遍历到第一项。

    var arr = [1, 2, 3, 4, 5];
    var rightResult = arr.reduceRight(function(prev, cur, index, self) {
        return prev + cur;
    });
    console.log(arr);  // [1, 2, 3, 4, 5]
    console.log(rightResult);  // 15