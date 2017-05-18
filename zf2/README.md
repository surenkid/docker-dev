# Zend Framework 2 自用开发环境

公司项目所使用的开发环境，集成ZendFrame2(PHP5.6) + MySQL5.7.16 + PostgreSQL9.0.22 + Solr5.5.4。

## 使用方法

git clone到本地后，终端进入到zf2目录下，输入：

  docker-composer up

## 恢复数据

下载代码及数据库数据备份包，复制到本机`~\docker_data`目录下。

脚本目前尚未做到完全智能，mysql与pgsql部分还需要手工导入，方法如下：

### 导入mysql备份

  docker exec -it MYSQL_CONTAINER_ID bash
  cd
  mysql -uroot -p
  create table zf2_mysql;
  set names utf8;
  source backup.sql
  
### 导入postgresql备份

  docker exec -it POSTGRES_CONTAINER_ID bash
  cd
  psql -U postgres
  create table zf2_pgsql;
  \q
  pg_restore -U postgres -d zf2_pgsql backup.tar
  
