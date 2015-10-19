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

That's it now our site is SQL injection free.

Cross-site Scripting (XSS):

i would say XSS is a pretty common hacking method and its important to you know how Cross-site Scripting works.
Cross-Site Scripting (XSS) is general hacking method used on websites it's normally based on the principal you can hide scripts behind urls and web pages.

For example,
URLs: www.kadhir.com?name=admin

web pages: code to be in script tags, If you go to web page it's not going to be visible but it will still run

Two Types of XSS:

	1.Persistent
	2.Non-Persistent

Non-Persistent will going to modify a client side information nothing is send to a database.

Persistent attack using web page(front end) you can store malicious code into back end, then it will send that malicious code to every user for each request.

This example user can store this script in DB, 
![_config.yml]({{ site.baseurl }}/images/php_securty/xss_attach1.png)

The simple way to protect XSS is don't simply store user data in DB and don't simply display in browser use htmlentities to validate user input before going to store and display. For example check below image

![_config.yml]({{ site.baseurl }}/images/php_securty/htmlentities.png)

That's it now you are pretty much safe from XSS. Of course if you are using framework it will take these things default, but i would say it's a good practice to do this one(at least keep in mind).

Next post we are going to look into "How to use Sublime Text IDE for more effectively - Especially Sublime Text3 on Mac"
Thanks, stay tuned!!