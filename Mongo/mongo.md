# mongo导入

* 使用mongo命令将数据库删除
	
	* use db_name;
	* db.dropDatabase()

* 导入（指定文件夹）数据

	* linux命令：mongorestore -d db_name 文件夹目录
	* windows命令：mongorestore.exe -d db_name 文件夹目录