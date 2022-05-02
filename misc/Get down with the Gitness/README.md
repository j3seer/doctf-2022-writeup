# Challenge description

Why. Is. There. Always. Another. File!!!

Author: AtomicNicos
-----------------------------------------------------------

Simple matroychka doll type challenge where alot of zip files are nested into each other until we get the flag

So with this script we can extract all the zip files until we get the BOMB_FLAG file which contains the flag

sol.py

```python3
# !/usr/bin/python3

import os



filename = "8fb0444894b78f857dd600b7f35c0af4.zip"
extract_dir = "ext"
flag = 0
while flag == 0:
        print("\n== Extracting ==\n")
        os.system("unzip {} -d {}".format(filename,extract_dir))
        if os.path.exists(extract_dir+"/base_images"):
                os.chdir(extract_dir+"/base_images")
        else:
                os.chdir(extract_dir)
        for file in os.listdir():
                if file.endswith("BOMB_FLAG"): 
                        # file.endswith("X"); ==> change X to whatever the final file name is , mine was BOMB_FLAG; 
                        # found the name from extracting until we find something different than a zip
                        print("\n== FLAG: ")
                        print(os.system("cat {}".format(file)))
                        flag = 1
                else:
                        filename = file



```

``` Flag : DOCTF{G00D_3FF0RT_BUT_1$_1T_0V3R?} ```

```
