---
layout: post
title: PHP:Protect Your Web From SQL Injection and XSS Attacks
---

Security in PHP
1.PHP Security - SQL Injection
2.PHP Security - XSS Attacks (Cross Site Scripting)

PHP Security_ SQL Injection:

if(isset($_POST['user'], $_POST['password'])){
	$user     = $_POST['user'];
	$password = $_POST['password'];

	$users = mysql_query("SELECT COUNT('user_id') FROM 'users' WHERE 'user_name' = '{$user}' AND 'user_password' = '{password}' ");
	$total = mysql_result($users, 0);
}

For example now user will to enter follwing value in text boxs User Name='admin' and password='****'

![_config.yml]({{ site.baseurl }}/images/Firtst_Post_2015-10-14.png)

Thanks, stay tuned!!