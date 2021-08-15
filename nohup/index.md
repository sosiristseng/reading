# nohup: Do not hang up in SSH sessions


`nohup` can run background process(es) uninterruptedly even a remote SSH session is offline.

```bash
nohup mycmd &
```

<!--more-->

The output will be in `nohup.out` by default. If you want to customize the output location, just redirect it:

```bash
nohup mycmd &> log.txt &
```

You can also lower the priority for the background process

```bash
nohup nice mycmd &
```

When you're done, you can kill the process by the proccess ID (PID)

```bash
ps -aux | grep "runoob.sh"

kill PID
```

**Sources**
- [Bird's Linux Manual](http://linux.vbird.org/linux_basic/0440processcontrol.php#nohup)
- [GT Wang](https://blog.gtwang.org/linux/linux-nohup-command-tutorial/)

