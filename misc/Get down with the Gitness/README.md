# Challenge description

Happy hunting!

https://github.com/punk-security/DOCON22_CTF1

Author: PunkSecurity
-----------------------------------------------------------

In this challenge we get a github repo that has alot of commits where he has the flag

So simply downloading the repo and going through the commits and grepping the flag format we get the flag

```bash
git clone https://github.com/punk-security/DOCON22_CTF1.git
git log --reverse -p | grep DOCTF{
```

![image](https://user-images.githubusercontent.com/58823465/166170846-06cd9bbb-079b-4b0d-855a-44214feb2d9f.png)


``` Flag : DOCTF{REDACTING_IN_GIT_IS_HARDZ} ```

