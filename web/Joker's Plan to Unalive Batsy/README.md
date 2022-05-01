# Challenge description

Why. Is. There. Always. Another. File!!!

Author: AtomicNicos
-----------------------------------------------------------

This challenge provided a page with a password input to login and a "forgot password" button

Clicking on that button we receive this message 

```One of your last passwords was 0e1137126905!```

==> PHP magic hashes !

So if we try that password we get this output

That means the password was changed to another php magic hash , so we can simply bruteforce this with a simple dictionnary i collected and using burpsuite

checking some of the responses we find the correct hash and the flag :

hash : 0e3583856241


``` Flag : DOCTF{MD5_H45_4_M4G1C4L_VULN3R4B1L1TY} ```

