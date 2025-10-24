# Reflected XSS into HTML with all tabs blocked except custom ones

 This lab blocks all HTML tags except custom ones.

To solve the lab, perform a cross-site scripting attack that injects a custom tag and automatically alerts document.cookie. 

____

### References

[https://portswigger.net/web-security/cross-site-scripting/cheat-sheet](https://portswigger.net/web-security/cross-site-scripting/cheat-sheet)

### Proof of Concept(Poc)

This the lab reflected xss into HTML with all tabs blocked except custom ones
![alt text()](images/Reflected%20XSS%20inr=to%20HTML%20context%20with%20all%20tags%20blocked%20except%20custom%20ones/image1.png)

---------
Try some tags is it allowed or not


![alt text()](images/Reflected%20XSS%20inr=to%20HTML%20context%20with%20all%20tags%20blocked%20except%20custom%20ones/image2.png)

------
But this not allowed

![alt text()](images/Reflected%20XSS%20inr=to%20HTML%20context%20with%20all%20tags%20blocked%20except%20custom%20ones/image3.png)

![alt text()](images/Reflected%20XSS%20inr=to%20HTML%20context%20with%20all%20tags%20blocked%20except%20custom%20ones/image4.png)


-----------
Now try on kintruder using all tags which are allowed and which are not
![alt text()](images/Reflected%20XSS%20inr=to%20HTML%20context%20with%20all%20tags%20blocked%20except%20custom%20ones/image5.png)



--------
custom tags are allowed


![alt text()](images/Reflected%20XSS%20inr=to%20HTML%20context%20with%20all%20tags%20blocked%20except%20custom%20ones/image6.png)


------
check the using custom tags it is allowed



![alt text()](images/Reflected%20XSS%20inr=to%20HTML%20context%20with%20all%20tags%20blocked%20except%20custom%20ones/image7.png)

---------
Now go to the exploit server and give payload in body section

![alt text()](images/Reflected%20XSS%20inr=to%20HTML%20context%20with%20all%20tags%20blocked%20except%20custom%20ones/image8.png)
