在使用 zabbix 4 时, orabbix 会报错:

	Orabbix - received unexpected response ' ' for key 'alive'

根据这个 [issue](https://github.com/smartmarmot/DBforBIX/issues/62),
修改了 `Sender.java`, 并把编译好的 class 文件, 添加到 orabbix-1.2.3.jar 中.
并打成了个 image.

我修改了build.sh，没有使用docker方式

cd orabbix

sh run.sh

## 使用方式

首先执行 `build.sh`, 这个脚本会编译 `Sender.java`, 并把 class 文件,添加到原来的
jar 包中, 放到 orabbix 目录下, 再打成一个 image `zabbix-agent-oralce`.

## Docker Environment Variables

- ZBX_SERVER_HOST zabbix server 地址, 默认为 127.0.0.1
- ZBX_SERVER_PORT zabbix server 端口, 默认为 10051
- ORACLE_HOST oralce 地址, 默认为 127.0.0.1
- ORACLE_PORT oralce 端口, 默认为 1521
- ORACLE_USER oralce 用户, 默认为 zabbix
- ORACLE_PASSWORD oralce 用户密码, 默认为 zabbix
- ORACLE_INSTANCE oralce 实例, 默认为 orcl
