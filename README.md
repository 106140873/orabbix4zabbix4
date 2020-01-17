作用：使用zabbix4支持监控oracle11g、Oracle12c

## 使用方式

这是根据 hsnotebook/orabbix4zabbix4 的项目修改的。


一、替换了ojdbc6.jar
   原来的ojadb6.jar只支持11g，使得12c的ojdbc6.jar进行替换

二、编译,我修改了build.sh，没有使用docker方式
sh build.sh
cd orabbix
sh run.sh
系统必需有java环境，如CENTOS7下要有：
java-1.8.0-openjdk-devel
java-1.8.0-openjdk-headless
java-1.8.0-openjdk

如果没有安装java-1.8.0-openjdk-devel，编译会提示找不到javac

ORACLE12默认只支持本地访问，除非切换为共享服务器模式
从安全角度建议orabbix放在被监控机上，配合zabbix-agent来实现监控的目的。

#config.props示例

cat config.props

ZabbixServerList=ZabbixServer1

ZabbixServer1.Address=ZabbixServerIP

ZabbixServer1.Port=10051

OrabbixDaemon.Sleep=300

OrabbixDaemon.MaxThreadNumber=100

DatabaseList=TESTDB1

DatabaseList.MaxActive=10

DatabaseList.MaxWait=100

DatabaseList.MaxIdle=1


TESTDB1.Url=jdbc:oracle:thin:@127.0.0.1:1521/orclpdb

TESTDB1.User=system

TESTDB1.Password=oracle

TESTDB1.MaxActive=10

TESTDB1.MaxWait=100

TESTDB1.MaxIdle=1

TESTDB1.QueryListFile=./conf/query.props


