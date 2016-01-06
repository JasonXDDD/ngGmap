# [IONIC] - 使用 navigation 結合 tabs

[TOC]


### 正文教學 :
- **DEMO : ** http://codepen.io/ionic/pen/odqCz?editors=101

#### (一)  JavaScript - ngRoute
一開使我們直接先設定Route來連結頁面，完成之後才會編輯HTML框架。
> **WHY: **
> 因為 angular 的 config 必須要把所有 url, template, controller...都設定好，也就是說，可以把 config 視為全部頁面的總覽，那之後要設計頁面就會相較容易。

-----
#####Angular config
```javascript
.config(function($stateProvider, $urlRouterProvider) {
	...
})
```
1. `$stateProvider` : 用來將頁面與 Angular 相連接
2. `$urlRouterProvider` : 指定URL連接相對頁面

--------
#####Setup states (tabs)
```javascript
// 'tabs' is the type of ionic tag
$stateProvider
	.state('tabs', {
		url: "/tab",
		abstract: true,
		templateUrl: "templates/tabs.html"
	})
```
1. `url` : 連結頁面的網址
2. `abstract` : 
3. `templateUrl/template` : 頁面的相對路徑

-------
#####Setup states (page)
```javascript
$stateProvider
	.state('tabs.home', {
		url: "/home",
		views: {
			'home-tab': {
				templateUrl: "templates/home.html",
				controller: 'HomeTabCtrl'
			}
		}
	})
```

----
#####Setup default page
```javascript
$urlRouterProvider.otherwise("/tab/home");
```

---
#### (二)  Ionic - navigation


### 參考連結 :
- **ionic-nav-view : ** http://ionicframework.com/docs/api/directive/ionNavView/
- **ionic-tabs : **  http://ionicframework.com/docs/api/directive/ionTabs/
- **angular-ui/ui-router : ** https://github.com/angular-ui/ui-router/wiki
