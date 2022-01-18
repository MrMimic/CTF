# CTF

## Cyber

### Gruyere

[Link to the app](http://google-gruyere.appspot.com/) 

#### Cross-Site Scripting (XSS)

##### Definition

Cross-site scripting (XSS) is a vulnerability that permits an attacker to inject code (typically HTML or JavaScript) into contents of a website not under the attacker's control. When a victim views such a page, the injected code executes in the victim's browser.

    - Reflected XSS attack: the attack is in the request itself (frequently the URL) and the vulnerability occurs when the server inserts the attack in the response verbatim or incorrectly escaped or sanitized. The victim triggers the attack by browsing to a malicious URL created by the attacker. 
    - Stored XSS attack, the attacker stores the attack in the application (e.g., in a snippet) and the victim triggers the attack by browsing to a page on the server that renders the attack, by not properly escaping or sanitizing the stored data.

If you can get JavaScript to execute on a page when it's viewed by another user, you have an XSS vulnerability.

##### Resources

[Gruyere](http://google-gruyere.appspot.com/part2)

##### Exploitation

    ```html
        <script>
        alert(document.cookie);
        </script>
    ```

This file, once uploaded and accessed, return all cookies informations from the current session.

Also, directly store the following somewhere it can be rendered back to the user:

    ```html
        <a ONMOUSEOVER="alert(1)" href="#">read this!</a>
    ```

The message is not excaped from the server, thus executed into the client's browser.

##### Fix

Host the content on a separate domain so the script won't have access to any content from your domain.

Always escape characters rendered from server side (`style='{{ color:text }}'`).
