# Stored DOM XSS
 This lab demonstrates a stored DOM vulnerability in the blog comment functionality. To solve this lab, exploit this vulnerability to call the alert() function.
___________________
 References:
 
[https://portswigger.net/web-security/cross-site-scripting/dom-based](https://portswigger.net/web-security/cross-site-scripting/dom-based)
 ____________
 Hah it is possible post a comments:

 
![Alt Text](Screenshot%202025-10-18%20151833.png)
 ______________
This generates the following html code:


 ![Alt Text (Description of the image)](image2.png)
 _______________

 We can try the payload:
 
</img src=1 onerror=alert()>
 ____________
 
 ![Alt Text (Description of the image)](image3.png)

 ___________
 It pops like this:

  ![Alt Text (Description of the image)](image.png)
 
 
 
