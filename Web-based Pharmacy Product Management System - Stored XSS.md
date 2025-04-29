# Web-based Pharmacy Product Management System - Stored XSS
+ **Exploit Title:** Web-based Pharmacy Product Management System - Stored XSS
+ **Date:** 2025-29-04
+ **Exploit Author:** Bora Hıdır
+ **Vendor Homepage:** [https://code-projects.org/online-book-system-in-php-css-js-and-mysql-free-download/](https://www.sourcecodester.com/php/17883/web-based-product-alert-system.html)
+ **Software Link:** [https://download.code-projects.org/details/74c24d93-431e-4e31-acc1-802f14caef5c](https://www.sourcecodester.com/php/17883/web-based-product-alert-system.html)
+ **Version:** 1.0
+ **Tested on:** Kali Linux + PHP/8.0.30, Apache 2.4.58
+ **CVE:** Reported, waiting for CVE number.

## Description:
The user added by Web-based Pharmacy Product Management System allows changing the username after logging in, and since this is not controlled in the database, a stored xss situation occurs.
When we examine the `edit-profile.php` file, we can see this situation.

## Proof of Concept:
+ Go to this address: "localhost/product_expiry/login.php"
+ We log in as admin with the given information and add a new user from the user management section.
![Ekran görüntüsü 2025-04-29 234441](https://github.com/user-attachments/assets/ec885c60-75c1-477a-b7af-e2848c8b0d34)
+ After creating a user, we log in with this user. this user is a plain user without any authorization.
+ After logging in, we come to the edit profile section from the user management section. In this section, we can change the fullname property and this is processed directly to the database and the vulnerability comes out from here. 
+ I update the fullname as `<script>alert('XSS')</script>` and save it.
![image](https://github.com/user-attachments/assets/e19d7a69-188b-44c5-a541-0cb1eded69f1)
+ And I see that it triggers the xss vulnerability, I can say that it is stored because I wrote it to the database.
![image](https://github.com/user-attachments/assets/897a83ac-bb81-430a-8a1b-9cd987f9d263)
+ Stored XSS Successful !
