---
layout: post
title: PHP:Protect Your Web From SQL Injection and XSS Attacks
---

PHP is a powerful language and the interpreter, whether included in a web server as a module or executed as a separate CGI binary, is able to access files, execute commands and open network connections on the server. These properties make anything run on a web server insecure by default. PHP is designed specifically to be a more secure language for writing CGI programs than Perl or C, and with correct selection of compile-time and runtime configuration options, and proper coding practices, it can give you exactly the combination of freedom and security you need.

Now we are just going to check how to protect our site form 
	1.SQL Injection and 
	2.XSS Attacks (Cross Site Scripting)

SQL Injection:
	Come, Let's deal with simple login authentication module, then our code probably looks like this

if(isset($_POST['user']) && isset($_POST['password'])){
	$user     = $_POST['user'];
	$password = $_POST['password'];

	$users = mysql_query("SELECT COUNT('user_id') FROM 'users' WHERE 'user_name' = '{$user}' AND 'user_password' = '{password}' ");
	$total = mysql_result($users, 0);
}

For example consider now user will going to enter follwing values in text boxs User Name='admin' and password='****'. 
In this case query will run like this,

	$users = mysql_query("SELECT COUNT('user_id') FROM 'users' WHERE 'user_name' = 'admin' AND 'user_password' = '****' ");

Now user will able to login successfully, everthing is going good.

What if user enter like this in text boxs User Name=admin' OR '1' = '1 and password = '****' else empty.

in this above case query will run like this

	$users = mysql_query("SELECT COUNT('user_id') FROM 'users' WHERE 'user_name' = 'admin' OR '1' = '1' AND 'user_password' = '' ");

'user_name' = 'admin' OR '1' = '1' which mean its always TRUE, then any one can login as admin in your site.
![_config.yml]({{ site.baseurl }}/images/Firtst_Post_2015-10-14.png)

Thanks, stay tuned!!