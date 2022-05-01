# Challenge description

Why. Is. There. Always. Another. File!!!

Author: AtomicNicos
-----------------------------------------------------------

This challenge provided a page with a password input to login and a "forgot password" button

![image](https://user-images.githubusercontent.com/58823465/166169958-bbdad928-9c6d-4bed-bed9-3adfc4b8c6d6.png)

Clicking on that button we receive this message 

```One of your last passwords was 0e1137126905!```

==> PHP magic hashes !

So if we try that password we get this output

![image](https://user-images.githubusercontent.com/58823465/166169969-5e46801c-b6ab-4e5c-9d45-dda9fa0b6fc1.png)

That means the password was changed to another php magic hash , so we can simply bruteforce this with a simple dictionnary i collected and using burpsuite

checking some of the responses we find the correct hash and the flag :

hash : 0e3583856241


![image](https://user-images.githubusercontent.com/58823465/166169983-94d66b34-4e4c-40ff-82e7-7bfa634e982b.png)


``` Flag : DOCTF{MD5_H45_4_M4G1C4L_VULN3R4B1L1TY} ```

