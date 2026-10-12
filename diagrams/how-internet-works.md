# How the Internet Works

This flow diagram illustrates the main steps involved when a user enters `example.com` in a web browser.

```text
+---------------------------+
| User enters example.com   |
| in the browser            |
+-------------+-------------+
              |
              v
+---------------------------+
| Browser/OS checks cache   |
| and resolves DNS if needed|
+-------------+-------------+
              |
              v
+---------------------------+
| Obtain server IP address  |
+-------------+-------------+
              |
              v
+---------------------------+
| Check routing table       |
| and default gateway       |
+-------------+-------------+
              |
              v
+---------------------------+
| Router forwards packets   |
| toward destination        |
+-------------+-------------+
              |
              v
+---------------------------+
| Secure connection setup   |
| and HTTP request          |
+-------------+-------------+
              |
              v
+---------------------------+
| Web server sends response |
+-------------+-------------+
              |
              v
+---------------------------+
| Browser renders webpage   |
+---------------------------+
```

## Key Points

- **DNS:** Helps resolve the domain name to an IP address.
- **IP and router:** Help deliver packets to the destination network.
- **TCP/IP and HTTPS:** Support network communication and secure web access.
- **Web server:** Responds to the browser's HTTP request.
- **Browser:** Processes the response and displays the webpage.