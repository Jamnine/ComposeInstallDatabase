<a name="ComposeInstallDatabase"></a>

# ComposeInstallDatabase

> Docker 数据库篇（MSSQL/MYSQL/POSTGRES）<br />使用 docker-compose 安装常用数据库

---

<a name="ptQYQ"></a>

## 🎖️ 系列文章

[Docker 安装相关工具](https://www.yuque.com/jamnine/coding/is03wz?view=doc_embed)

---

<a name="658b4cfd"></a>

## 🎖️ 使用教程

<a name="x9gKB"></a>

### 🚩 进入需要安装的存放位置

```shell
cd /home/docker
```

<a name="f1ce1947"></a>

### 🚩 clone 项目

```shell
https://github.com/Jamnine/ComposeInstallDatabase.git
```

<a name="469747f0"></a>

### 🚩 编辑 docker-compose.yml，默认安装 6 个版本数据库

-   [x] SQL SERER 2017
-   [x] SQL SERER 2019
-   [x] SQL SERER 2022
-   [x] MYSQL 5.7.28
-   [x] MYSQL 8.0.28
-   [x] POSTGRES 14.6

如果只要开启一个 MySQL8，则注释其他即可

```yaml
# version: '3.3'
# services:
mysql8:
    restart: always
    container_name: mysql-8.0.28
    volumes:
        - './mysql-8.0.28/mysql.cnf:/etc/mysql/conf.d/mysql.cnf:ro'
        - './mysql-8.0.28/data:/var/lib/mysql/:rw'
        - './mysql-8.0.28/logs:/var/log/mysql/:rw'
    ports:
        - '3599:3306'
    environment:
        - TZ=Asia/Shanghai
        - MYSQL_ROOT_HOST=%
        - MYSQL_ROOT_PASSWORD=nine_123456
    image: 'mysql/mysql-server:8.0.28'
#     mysql5:
#         restart: always
#         container_name: mysql-5.7.28
#         volumes:
#             - './mysql-5.7.28/mysql.cnf:/etc/mysql/conf.d/mysql.cnf:ro'
#             - './mysql-5.7.28/data:/var/lib/mysql/:rw'
#             - './mysql-5.7.28/logs:/var/log/mysql/:rw'
#         ports:
#             - '3598:3306'
#         environment:
#             - TZ=Asia/Shanghai
#             - MYSQL_ROOT_HOST=%
#             - MYSQL_ROOT_PASSWORD=nine_123456
#         image: 'mysql/mysql-server:5.7.28'

#     mssql2022:
#         restart: always
#         container_name: mssql-2022
#         user: root
#         volumes:
#             - './mssql-2022:/var/opt/mssql'
#         ports:
#             - '3597:1433'
#         environment:
#             - TZ=Asia/Shanghai
#             - ACCEPT_EULA=Y
#             - SA_PASSWORD=nine_123456
#             - MSSQL_LCID=2052
#             - MSSQL_COLLATION=Chinese_PRC_CI_AS
#         image: 'mcr.microsoft.com/mssql/server:2022-latest'

#     mssql2019:
#         restart: always
#         container_name: mssql-2019
#         user: root
#         volumes:
#             - './mssql-2019:/var/opt/mssql'
#         ports:
#             - '3596:1433'
#         environment:
#             - TZ=Asia/Shanghai
#             - ACCEPT_EULA=Y
#             - SA_PASSWORD=nine_123456
#             - MSSQL_LCID=2052
#             - MSSQL_COLLATION=Chinese_PRC_CI_AS
#         image: 'mcr.microsoft.com/mssql/server:2019-latest'

#     mssql2017:
#         restart: always
#         container_name: mssql-2017
#         volumes:
#             - './mssql-2017:/var/opt/mssql'
#         ports:
#             - '3595:1433'
#         environment:
#             - TZ=Asia/Shanghai
#             - ACCEPT_EULA=Y
#             - SA_PASSWORD=nine_123456
#             - MSSQL_LCID=2052
#             - MSSQL_COLLATION=Chinese_PRC_CI_AS
#         image: 'mcr.microsoft.com/mssql/server:2017-latest'

#     postgres14.6:
#         restart: always
#         container_name: postgres-14.6
#         volumes:
#             - './postgres-14.6/data:/var/lib/postgresql/data'
#         ports:
#             - '3594:5432'
#         environment:
#             - TZ=Asia/Shanghai
#             - POSTGRES_PASSWORD=nine_123456
#             - ALLOW_IP_RANGE=0.0.0.0/0
#         image: 'postgres:14.6'
```

<a name="RZBUa"></a>

### 🚩 执行构建

```shell
docker-compose up 或 docker-compose up -d (返回ID)
```
