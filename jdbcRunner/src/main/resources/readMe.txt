一、编译说明
	1、本项目默认添加Oracle、MySQL的数据库驱动，如需添加其他JDBC驱动，自行在项目的pom.xml文件中添加。
	
	2、如果需要连接Oracle，需要本地Maven仓库或私服安装Oracle Jdbc驱动。
	如果已经安装，替换pom.xml里面的oracle驱动坐标。
	如果没有，需要安装驱动到本地maven仓库。
		1、下载Oracle数据库驱动（建议使用ojdbc6.jar），这里使用ojdbc6为例子。
		2、定位到ojdbc6.jar所在目录，执行下面maven脚本（Dversion参数对应下载的驱动版本）：
		mvn install:install-file -Dfile=ojdbc6.jar -DgroupId=com.oracle -DartifactId=ojdbc6 -Dversion=11.2.0.1.0 -Dpackaging=jar

2、
	