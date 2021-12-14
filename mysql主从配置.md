## **主数据库配置**
```
log-bin = mysql-bin
server-id = 1
binlog_format = mixed
binlog-do-db=test  //需要同步的数据库
```
## **从数据库配置**

```
log-bin = mysql-bin
server-id =2
binlog_format = mixed
replicate-do-db=test //需要同步的数据库
```

 
 

## **主库操作**

```
1. use test;
2. flush tables with read locks;
3. mysqldump -u root -p test > test_db.sql//导出主库的数据库
4. show master status;
5. 记录一下| File | Position
6. unlock tables;
7.  
```

## **从库操作**
```
把test_db.sql数据导入从库
change master to master_host='主库的ip',
master_port=主库的端口,
master_user='root',
master_password='123456',
master_log_file='binlog的file',
master_log_pos=binlog的Position;
show slave status;
start slace;
```



[参考文章https://note.youdao.com/](https://note.youdao.com/)



 




 
