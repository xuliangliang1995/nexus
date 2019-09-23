提供 nexus 最新版下载链接（上次更新时间：2019-09-23）
* 本人用的阿里云OSS存储，下载很快，但是本人会为流量付费，所以，请不要恶意重复下载。

## nexus-3.18.1-01 
* Linux 下载地址：https://nexus-bucket.oss-cn-beijing.aliyuncs.com/nexus-3.18.1-01-unix.tar.gz
* Windwos 下载地址：https://nexus-bucket.oss-cn-beijing.aliyuncs.com/nexus-3.18.1-01-win64.zip

## nexus maven 私服部署参考
1. 安装 Nexus , 这里以 Centos 7 为例。

   国内下载 Nexus 非常慢，这里提供了自己的：[Nexus下载指引](https://github.com/xuliangliang1995/nexus)

   ```shell
   # 下载 Nexus（这个链接是我自己的，下载很快，可以直接使用）
   wget https://nexus-bucket.oss-cn-beijing.aliyuncs.com/nexus-3.18.1-01-unix.tar.gz
   # 解压
   tar -zxvf nexus-3.18.1-01-unix.tar.gz
   # 解压后会有两个目录，一个是 nexus-3.18.1-01，另一个是sonatype-work
   cd nexus-3.18.1-01/bin/
   
   # 注意有一个文件 nexus.vmoptions，里面信息如下，如果移动包路径注意修改这里面的配置
   	 -Xms2703m
       -Xmx2703m
       -XX:MaxDirectMemorySize=2703m
       -XX:+UnlockDiagnosticVMOptions
       -XX:+UnsyncloadClass
       -XX:+LogVMOutput
       -XX:LogFile=../sonatype-work/nexus3/log/jvm.log
       -XX:-OmitStackTraceInFastThrow
       -Djava.net.preferIPv4Stack=true
       -Dkaraf.home=.
       -Dkaraf.base=.
       -Dkaraf.etc=etc/karaf
       -Djava.util.logging.config.file=etc/karaf/java.util.logging.properties
       -Dkaraf.data=../sonatype-work/nexus3
       -Djava.io.tmpdir=../sonatype-work/nexus3/tmp
       -Dkaraf.startLocalConsole=false
       
   # 前台启动
   sh nexus run 
   # 后台启动
   sh nexus start
   # 终止命令
   sh nexus stop
   
   # 默认监听 8081 端口，启动后稍等片刻可以通过 http://ip:8081 进行访问
   # 如果访问不了，则去 soantype-work 包中去找 log 文件查看
   # 默认初始密码存储地址：sonatype-work/nexus3/admin.password，用户名：admin
   ```

2. 配置仓库（[参考文档](https://blog.csdn.net/qq_28666081/article/details/83270713)）

3. Maven settings.xml 配置（[参考文档](https://www.cnblogs.com/qdhxhz/p/9808642.html)）

4. 上面放了一份 setting.xml 可供参考。
   
