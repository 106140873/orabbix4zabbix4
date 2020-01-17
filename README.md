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
