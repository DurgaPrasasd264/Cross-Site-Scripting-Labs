# Reflected XSS into HTML Context with Most Tags and Attributes Blocked

This lab contains a **reflected XSS vulnerability** in the search functionality but uses a **Web Application Firewall (WAF)** to protect against common XSS vectors.  

**Objective:** Perform a cross-site scripting attack that bypasses the WAF and calls the `print()` function.

---

## References

- [PortSwigger XSS Cheat Sheet](https://portswigger.net/web-security/cross-site-scripting/cheat-sheet)
- [Exploiting Reflected XSS](https://portswigger.net/web-security/cross-site-scripting/exploiting)

---

## Proof of Concept (PoC)

### Step 1: Search Something
The search functionality reflects input like this:

![Search Reflection](images/Reflected%20XSS%20into%20HTML/image1.png)

---

### Step 2: Test HTML Tags
Testing the `img` tag:

![Img Tag Blocked](images/Reflected%20XSS%20into%20HTML/image2.png)

Observation: **`img` tag blocked by WAF**

![Blocked Tag](images/Reflected%20XSS%20into%20HTML/image3.png)

---

### Step 3: Intercept Request
Send the request to Burp Suite for testing:

![Burp Suite](images/Reflected%20XSS%20into%20HTML/image4.png)

---

### Step 4: Identify Allowed Tags
Check which tags are allowed using [PortSwigger XSS Cheat Sheet](https://portswigger.net/web-security/cross-site-scripting/cheat-sheet):

![Allowed Tags](images/Reflected%20XSS%20into%20HTML/image5.png)

Copy allowed tags for use as payloads in Burp Intruder:

![Payload Setup](images/Reflected%20XSS%20into%20HTML/image6.png)

---

### Step 5: Use Body Tag
- The `<body>` tag is **not blocked**.
- Custom tags are also allowed but are treated as alphanumeric strings.

![Body Tag Allowed](images/Reflected%20XSS%20into%20HTML/image7.png)

---

### Step 6: Identify Allowed Events
Use the cheat sheet to find allowed events for `<body>`:

![Allowed Events](images/Reflected%20XSS%20into%20HTML/image8.png)

---

### Step 7: Add Event Payload
Give the allowed event as a payload to `<body>` tag:

![Event Payload](images/Reflected%20XSS%20into%20HTML/image9.png)

Observation: Some events are blocked, so we use the **`onsize`** event with `<body>`.

---

### Step 8: Final Payload
The final payload to bypass WAF and execute `print()`:
https://0a3600710393b2d6805f3f4000c00040.web-security-academy.net/?search=\%27-alert(1)//

![Final Payload](images/Reflected%20XSS%20into%20HTML/image10.png)

Success:

![XSS Triggered](images/Reflected%20XSS%20into%20HTML/image11.png)

---

## Notes
- WAF blocks common tags (`img`, `script`, etc.), but `<body>` is allowed.
- Using **allowed events** is key to bypassing WAF.
- Custom tags are treated as alphanumeric, so not useful for script execution.
- Always check the [PortSwigger XSS Cheat Sheet](https://portswigger.net/web-security/cross-site-scripting/cheat-sheet) for allowed HTML/JS context payloads.

---

## Status
✅ **Lab Completed**









https://0a3600710393b2d6805f3f4000c00040.web-security-academy.net/?search=\%27-alert(1)//
