# Expect scp example
+ ref : http://www.zedwood.com/article/linux-scp-expect-script
+ script
```
#!/usr/bin/expect

set PASS "mypwd"
set timeout -1

spawn scp ~/somedir/somefile usr@192.168.10.10:~/otherdir

expect {
        password: {send "$PASS\r" ; exp_continue}
        eof exit
}
```