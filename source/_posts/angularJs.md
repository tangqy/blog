---
title: angularJs
date: 2017-01-05 21:35:23
tags: angular
---
# <center>angularJs的纪录</center>
### angular router
在angular路由中我们有时需要根据路由动态配置对应的controller，比如
<pre>
$stateProvider
    .state('foo', {
        url: '/foo/:bar',
        templateUrl: 'some-template-path.html',
        resolve : {
            getController : function($stateParams){
                if ($stateParams.bar === "tab1") {

                    return "tab1Controller"

                }else if ($stateParams.bar === "tab2") {

                    return "tab2Controller"

                }else if ($stateParams.bar === "tab3"){

                    return "tab3Controller"

                }else if ($stateParams.bar === "tab4") {

                    return "tab4Controller"

                }
            }
        },
        controllerProvider: function(getController){
            return getController;
        }
 </pre>
 
 也可以用这样的方式：
 <pre>
 	$stateProvider
		.state("/Dashboards/:dashboardName",{
   			templateUrl:function($stateParams) {
         		return "Dashboards/" + $stateParams.dashboardName;
       		},
   			controllerProvider: function($stateParams) {
         		return $stateParams.dashboardName+"Controller";
       		}
  	})
 </pre>
 [具体细节可以参考这里](http://stackoverflow.com/questions/18423054/dynamically-loading-the-controller-in-angularjs-routeprovider)