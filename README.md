# 一、开发背景
1. 项目规模不大，只用到Servlet，需要使用JDBC进行数据访问。存在以下不方便地方：
*JDBC访问数据需要每次手动关闭Statement、ResultSet、Connection等JDBC操作对象；*

# 二、jdbcRunner作用
1. 封装JDBC操作对象，实现自动关闭JDBC操作对象。
2. 通过日志配置是否输出SQL语句。
3. 简化JDBC编码，一般只需要SQL语句，参数，返回值的自我封装方式，即可。
4. 提供Connection，用户可以自行写原始JDBC原始访问操作。
5. 使用DBCP2作为数据库连接池，透明化数据库连接。

# 三、编译说明
1. 本项目默认添加Oracle、MySQL的数据库驱动，如需添加其他JDBC驱动，自行在项目的pom.xml文件中添加。
2. 如果需要连接Oracle，需要本地Maven仓库或私服安装Oracle Jdbc驱动。
3. 如果已经安装，替换pom.xml里面的oracle驱动坐标。
4. 如果没有，需要安装驱动到本地maven仓库。
a、下载Oracle数据库驱动（建议使用ojdbc6.jar），这里以安装11.2.0.1.0版本的ojdbc6为例子。
b、定位到ojdbc6.jar所在目录，执行下面maven脚本（Dversion参数对应下载的驱动版本）：
`mvn install:install-file -Dfile=ojdbc6.jar -DgroupId=com.oracle -DartifactId=ojdbc6 -Dversion=11.2.0.1.0 -Dpackaging=jar`

# 四、使用说明
## 1、主要类
1. JdbcRunner：JDBC访问入口，提供常用的访问方法。
2. ransaction：JDBC事物管理。
3. JdbcManageer：JDBC管理。作为JdbcRunner和Transaction的工厂。
4. SqlLogger：SQL语句和参数的输出，通过配置此类的log4j输出，控制项目SQL语句输出。
## 2、使用
见test源目录的demo包。
