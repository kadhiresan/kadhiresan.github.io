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

	![_config.yml]({{ site.baseurl }}/images/php_securty/php_sec1.png)

For example consider now user will going to enter following values in text boxes User Name='admin' and password='****'.
In this case query will run like this,

	![_config.yml]({{ site.baseurl }}/images/php_securty/query1_normal.png)

Now user will able to login successfully, everything's going good.

What if user enter like this in text boxes User Name=admin' OR '1' = '1 and password = '****' else empty.

in this above case query will run like this

	![_config.yml]({{ site.baseurl }}/images/php_securty/query2_hack.png)

'user_name' = 'admin' OR '1' = '1' which mean it's always TRUE, then any one can login as admin in your site.

So now we are going to handle this bad situation using PHP "mysql_real_escape_string" function and for password i am going to use md5() (you can use hash(), sha1() and lot more)

	![_config.yml]({{ site.baseurl }}/images/php_securty/php_sec2.png)

Thanks, stay tuned!!