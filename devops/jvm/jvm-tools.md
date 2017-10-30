# JVM Tools


## JVM 监控工具

### jstack

```
jstack -h

> -F 强制, dump 挂起的进程
> -m java 和　native frame
> -l long running

1. 查看 Java 进程　pid
ps -ef | grep java

2. jstack pid
```


### jvisualvm

```
jvisualvm

1. 监控之前添加 JVM 参数　JAVA_OPTS=
 -Dcom.sun.management.jmxremote.port=10086 -Dcom.sun.management.jmxremote.ssl=false -Dcom.sun.management.jmxremote.authenticate=false -Djava.rmi.server.hostname=192.168.1.101
 
根据需要修改 port 和　hostname

2. 添加远程主机, hostname:port, JMX

3. 双击打开


```

### JProfiler

### YourKit Java Profiler