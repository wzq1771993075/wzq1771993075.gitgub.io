---
layout: post
title: JavaScript编程题-字符串
category: 资源
---
## 写一个字符串转成驼峰的方法？

#### ①字符串法：
        function test(str){
            var arr = str.split('-');
            for(var i=1;i<arr.length;i++){
                arr[i] = arr[i].charAt(0).toUpperCase() + arr[i].substring(1);
            }
            return arr.join('');
        }
        console.log(test('border-bottom-color'));

#### ②正则表达式法：
    
        function test(str){
            var re = /-(\w)/g;
            return str.replace(re,function($0,$1){
                //$0代表匹配项，$1指的是第一个捕获组的子字符串
                //必须写上$0--replace函数规定的参数
                return $1.toUpperCase();
                });
        }
        console.log(test('border-bottom-color'));

## 查找字符串中出现最多的字符和个数？

#### ①字符串法： 
        function test(str){
            var obj = {};
            var max = 0;
            var value = null;
            for(var i=0;i<str.length;i++){
                if(!obj[ str[i] ]){
                    obj[ str[i] ] = [];
                    obj[ str[i] ].push(str[i]);
                }else{
                    obj[ str[i] ].push(str[i]);
                }
            }
            for(var attr in obj){
                if(max < obj[attr].length){
                    max = obj[attr].length;
                    value = obj[attr][0];
                }
            }
            return '出现最多的字符是：' + value + '，个数为：' + max ;
        }
        console.log(test('asdaasaaf'));

#### ②正则表达式法：
        function test(str){
            var max = 0,value = null;
            //进行排序，目的是把相同的字符放在一起
            var arr = str.split('');
            arr.sort();
            str = arr.join('');
            //开始匹配
            var re = /(\w)\1+/g;
            // \n的意思是：和第n个分组第一次匹配的字符相匹配
            str.replace(re,function($0,$1){
                if(max < $0.length){
                    max = $0.length;
                    value = $1;
                }
            });
           return '出现最多的字符是：' + value + '，个数为：' + max ;
                
         }
         console.log(test('border-bottom-color'));

## 如何给字符串加千分符？

#### ①字符串法： 
          function test(str){
            var iNum = str.length%3;
            var prev = '';
            var arr = [];
            var iNow = 0;
            var temp = '';
            //非3的整数倍，截断
            if(iNum != 0){
                prev = str.substring(0,iNum);
                arr.push(prev);
            }
            str = str.substring(iNum);
            for(var i=0;i<str.length;i++){
                iNow++;
                temp += str[i];
                if(iNow == 3 && temp){
                    arr.push(temp);
                    iNow = 0;
                    temp = '';
                }
            }
            return arr.join(',');
         }
         console.log(test('1245624764571'));

#### ②正则表达式法：
        function test(str){
            //此处的正则表达式略复杂
            //(?=p)前向声明
            //要求接下来的字符都与p匹配，但不能包含匹配p的那些字符
            //(?!p)反前向声明，要求接下来的字符不与p匹配
            var re = /(?=(?!\b)(\d{3})+$)/g;
            return str.replace(re,',');
        }
        console.log(test('213142543563'));


