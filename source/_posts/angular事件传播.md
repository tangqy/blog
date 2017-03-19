---
title: angular事件传播
date: 2017-01-07 00:21:11
tags: angular
---
### <center>angular提供了$emit，$broadcast，$on服务用于scope之间的交流</center>
###### $emit

$emit是由子scope往rootScope传播事件，向上分发事件。语法为：

	$scope.$emit(eventName,data);

###### $broadcast 

$broadcast事件是父级scope往子scope传播，向下广播事件。语法为：

	$scope.$broadcast(eventName,data);

###### $on 

$on：监听或接收数据。用于接收向上分发或者是向下广播事件的event与data。语法为

	$scope.$on(eventName,function(event,data){
			//do sth 
	});

$on的方法中的event事件参数：
    event.name 事件名称
    event.targetScope  发出或者传播原始事件的作用域
    event.currentScope 目前正在处理的事件的作用域

    event.stopPropagation()    一个防止事件进一步传播(冒泡/捕获)的函数(这只适用于使用`$emit`发出的事件)
    event.preventDefault() 这个方法实际上不会做什么事，但是会设置`defaultPrevented`为true。直到事件监听器的实现者采取行动之前它才会检查`defaultPrevented`的值。
    event.defaultPrevented 如果调用了`preventDefault`则为true
