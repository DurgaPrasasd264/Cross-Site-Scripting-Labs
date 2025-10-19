# Reflected XSS into HTML context with most tags and attributes blocked

 This lab contains a reflected XSS vulnerability in the search functionality but uses a web application firewall (WAF) to protect against common XSS vectors.

To solve the lab, perform a cross-site scripting attack that bypasses the WAF and calls the print() function. 

******
References:

[https://portswigger.net/web-security/cross-site-scripting/cheat-sheet](https://portswigger.net/web-security/cross-site-scripting/cheat-sheet)

[https://portswigger.net/web-security/cross-site-scripting/exploiting](https://portswigger.net/web-security/cross-site-scripting/exploiting)



# Proof of Concept(PoC):

search something it shows like this

![alt text ()](images/Reflected%20XSS%20into%20HTML/image1.png)


Now i searched the html tag that is imag tag

![alt text ()](images/Reflected%20XSS%20into%20HTML/image2.png)

Ohh! the img tag blocked

![alt text ()](images/Reflected%20XSS%20into%20HTML/image3.png)

Than the request send into burpsuite 

![alt text ()](images/Reflected%20XSS%20into%20HTML/image4.png)

next check tags which tags are blocked and which are not it takes from the  [https://portswigger.net/web-security/cross-site-scripting/cheat-sheet](https://portswigger.net/web-security/cross-site-scripting/cheat-sheet)

![alt text ()](images/Reflected%20XSS%20into%20HTML/image5.png)

Copy the tags and it uses as a payloads in intruder 

![alt text ()](images/Reflected%20XSS%20into%20HTML/image6.png)


 We known the body and custom tags are not blocked so we take body tag because of custom tags are not html it is just alphanumeric strings

 
![alt text ()](images/Reflected%20XSS%20into%20HTML/image7.png)

We decide that body tag is not blocked so we find the events which are allowed.It takes from the  [https://portswigger.net/web-security/cross-site-scripting/cheat-sheet](https://portswigger.net/web-security/cross-site-scripting/cheat-sheet)


![alt text ()](images/Reflected%20XSS%20into%20HTML/image8.png)

next we give this events as a payload beside of body

![alt text ()](images/Reflected%20XSS%20into%20HTML/image9.png)

Now some events are allowed but instead of that onsize is used the event of body tag and Finaly this is the payload of this

![alt text ()](images/Reflected%20XSS%20into%20HTML/image10.png)



![alt text ()](images/Reflected%20XSS%20into%20HTML/image11.png)
