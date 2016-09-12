一、启动consul

（1个server+1个client，方便起见，client使用本机）：查看：http://www.cnblogs.com/java-zhao/p/5375132.html

1、开启虚拟机-->切换到vagrantFile中配置的节点

vagrant up
vagrant ssh n110
2、启动server（n110）

consul agent -server -bootstrap-expect=1  -data-dir=tmp/consul -node=server-110 -bind=192.168.0.112 -dc=zjgdc1 -client 0.0.0.0 -ui

说明：-client 0 0 0 0 -ui-->使得客户端可以直接通过url访问服务端的consul ui

3、启动client（local）

consul agent -data-dir=/tmp/consul -node=client-my -bind=xxx -dc=zjgdc1
说明：xxx代表本机IP

4、client加入server

consul join 192.168.21.110