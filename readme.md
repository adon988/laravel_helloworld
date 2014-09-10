## Laravel PHP Framework

[![Build Status](https://travis-ci.org/laravel/framework.svg)](https://travis-ci.org/laravel/framework)
[![Total Downloads](https://poser.pugx.org/laravel/framework/downloads.svg)](https://packagist.org/packages/laravel/framework)
[![Latest Stable Version](https://poser.pugx.org/laravel/framework/v/stable.svg)](https://packagist.org/packages/laravel/framework)
[![Latest Unstable Version](https://poser.pugx.org/laravel/framework/v/unstable.svg)](https://packagist.org/packages/laravel/framework)
[![License](https://poser.pugx.org/laravel/framework/license.svg)](https://packagist.org/packages/laravel/framework)

Laravel is a web application framework with expressive, elegant syntax. We believe development must be an enjoyable, creative experience to be truly fulfilling. Laravel attempts to take the pain out of development by easing common tasks used in the majority of web projects, such as authentication, routing, sessions, and caching.

Laravel aims to make the development process a pleasing one for the developer without sacrificing application functionality. Happy developers make the best code. To this end, we've attempted to combine the very best of what we have seen in other web frameworks, including frameworks implemented in other languages, such as Ruby on Rails, ASP.NET MVC, and Sinatra.

Laravel is accessible, yet powerful, providing powerful tools needed for large, robust applications. A superb inversion of control container, expressive migration system, and tightly integrated unit testing support give you the tools you need to build any application with which you are tasked.

## Official Documentation

Documentation for the entire framework can be found on the [Laravel website](http://laravel.com/docs).

### Contributing To Laravel

**All issues and pull requests should be filed on the [laravel/framework](http://github.com/laravel/framework) repository.**

### License

The Laravel framework is open-sourced software licensed under the [MIT license](http://opensource.org/licenses/MIT)


Laravel 安裝教學 (以xampp為例)

1. 必須先確定有安裝composer
     請參考Composer安裝教學

2. 打開terminal (cmd)進入 webserver資料夾

(ex .   cd xampp/htdocs/)

3. 安裝Laravel

終端機輸入:
	 composer create-project laravel/laravel

4. 安裝成功，應該會看到laravel資料夾，其中包含以下結構


加入 .htaccess
	laravel根目錄加入.htaccess ，包含以下內容
Options +FollowSymLinks
RewriteEngine On

RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^(.+)/$ http://%{HTTP_HOST}/$1 [R=301,L]

RewriteCond %{REQUEST_FILENAME} !-f
RewriteRule ^ index.php [L]


網址欄輸入
http://localhost:82/laravel/public/

移除public
將public資料全部移除資料夾
打開index.php調整路徑:
	require __DIR__.'/bootstrap/autoload.php';
	$app = require_once __DIR__.'/bootstrap/start.php';

調整bootstrap/paths.php路徑
'public' => __DIR__.'/..',	

網址欄輸入
http://localhost:82/laravel/


設定路由:
laravel/app/routes.php


方法一、直接從路由顯示view
Route::get('/test', function()
{
	return View::make('test');
});


	view 直接新增 test.php

方法二、傳給controller

	輸入以下程式碼:(我們預計會帶入id)
	Route::get('user/{id}', 'UserController@showProfile');

	controller 內容:
	(在showProfile會接收$id)

view 內容:

(此範例直接使用 laravel 的 Blade 樣版引擎，他是由簡單的正則表示式以及單純的PHP對樣板進行編譯，速度非常快。)

新增 layout.blade.php (母版)
新增 user.blade.php (子版)


layout.blade.php內容



user.blade.php內容


