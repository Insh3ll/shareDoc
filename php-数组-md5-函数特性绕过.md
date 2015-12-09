title: 'php-$_GET数组,md5()函数特性绕过'
date: 2015-12-05 13:01:28
tags: [php,md5,ctf,数组,绕过]
---
在做到一个ctf时看到这样的一个题目
```
if (isset($_GET['a']) and isset($_GET['b'])) 
    if ($_GET['a'] != $_GET['b'])
    	if (md5($_GET['a']) === md5($_GET['b']))
        	die('Flag: '.$flag);
    else
        print 'Wrong.';
```
开始没注意到 `===` 以为是利用php md5()函数的漏洞  
```
<?php 
var_dump(md5('240610708') == md5('QNKCDZO')); 
var_dump(md5('aabg7XSs') == md5('aabC9RqS')); 
?>
```
无果后看到 `===`,真要找md5碰撞??   
后来队友提醒用数组绕过
>http://xxxx.com/web.php?a[]=1&b[]=2

成功拿到Flag  

后来自己测试时发现在第二个if处`if ($_GET['a'] != $_GET['b'])`时,因为此时a跟b是两个数组,而两个数组内容不一样,所以为True.到第三个if时`if (md5($_GET['a']) === md5($_GET['b']))`,直接$_GET['a']得到的是`Array`,$_GET['b']也是一样`Array`,所以`md5(Array) === md5(Array)`成功绕过
