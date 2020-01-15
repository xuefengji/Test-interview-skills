# Linux 操作系统

1、如何动态查看文件中你关心的内容，比如error信息

tail -f xxx.log | grep error

2、如何跨服务器拷贝你的文件

scp -r 

3、超大文件在跨服务器拷贝过程中，经常断开，你是怎么解决的

rsync

4、文件查看常用命令有什么？请讲述他们的区别

tail  more less  cat

5、如何去除文件中的重复行

cat  data | sort | uniq

6、如何通过监控命令查看服务器的平均负载值

