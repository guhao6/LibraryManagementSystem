由于文件较大，如果可以还请下载压缩包进行查看，造成不便，还请见谅

图书管理系统
基于 JSP + Servlet + MySQL 实现的 JavaWeb 课程设计 / 毕业设计
一、项目介绍
本项目是一套功能完整、界面美观、结构清晰的图书管理系统。系统以借阅统计为核心模块，实现图书管理、用户管理、标签管理、借阅管理、借阅数据统计、热门图书排行、逾期统计等一体化功能。
前端采用科技风首页 + 粉色清新操作页面，交互友好、操作简单。后端使用经典 JavaWeb 技术栈，适合课程设计、毕业设计、学习演示。
开发团队：永无 Bug 队系统版本：v2.0.7运行状态：OPERATIONAL（正常运行）
二、功能模块
1. 图书管理
图书信息新增、修改、删除、查询
支持图书名称、作者、出版社、标签管理
支持图书搜索、快速定位
2. 用户管理
用户信息：用户名、学号、手机号、邮箱
支持按用户名、学号搜索
用户新增、编辑、删除
3. 标签管理
图书标签分类（教材、文学、科技、小说等）
标签添加、修改、删除、搜索
4. 借阅管理（核心功能）
借书：输入用户 ID + 图书 ID
归还：一键归还
借阅记录展示：借阅时间、归还时间、状态
支持按学号、书名检索借阅记录
5. 借阅统计中心
当前借阅中数量统计
逾期未还数量统计
借阅总量统计
热门图书 TOP10 借阅排行
图书借阅次数统计
数据可视化展示
三、技术栈
前端：JSP、HTML、CSS、JavaScript后端：Java、Servlet、JDBC服务器：Tomcat 8.5 及以上数据库：MySQL 5.7 / 8.0开发工具：IntelliJ IDEA、Navicat
四、数据库设计
1. 创建数据库
CREATE DATABASE IF NOT EXISTS library;USE library;
2. 用户表
CREATE TABLE user (id INT PRIMARY KEY AUTO_INCREMENT,username VARCHAR(50) NOT NULL,student_id VARCHAR(50) UNIQUE NOT NULL,phone VARCHAR(20),email VARCHAR(50));
3. 标签表
CREATE TABLE tag (id INT PRIMARY KEY AUTO_INCREMENT,tag_name VARCHAR(30) NOT NULL);
4. 图书表
CREATE TABLE book (id INT PRIMARY KEY AUTO_INCREMENT,book_name VARCHAR(100) NOT NULL,author VARCHAR(50),publish VARCHAR(100),tag_id INT,count INT DEFAULT 0);
5. 借阅表
CREATE TABLE borrow (id INT PRIMARY KEY AUTO_INCREMENT,user_id INT NOT NULL,book_id INT NOT NULL,borrow_time DATETIME NOT NULL,return_time DATETIME,status INT NOT NULL -- 0 = 借阅中 1 = 已归还 2 = 逾期);
五、借阅统计核心 SQL
1. 统计当前借阅中数量
SELECT COUNT(*) FROM borrow WHERE status = 0
2. 统计逾期未还数量
SELECT COUNT(*) FROM borrow WHERE status = 2
3. 热门图书 TOP10 排行
SELECT book.book_name, COUNT(*) AS borrow_countFROM borrowJOIN book ON borrow.book_id = book.idGROUP BY book_idORDER BY borrow_count DESCLIMIT 10
4. 查询所有借阅记录
SELECT * FROM borrow ORDER BY borrow_time DESC
六、项目部署步骤
创建数据库 library
执行数据库 SQL 脚本
导入项目到 IDEA / Eclipse
修改数据库连接配置（账号、密码）
部署到 Tomcat
启动访问：http://localhost:8080/index.jsp
七、系统界面说明
首页：深色科技风格，五大功能入口
标签管理：粉色清新界面，支持搜索与编辑
用户管理：用户信息列表，支持增删改查
借阅管理：借阅记录展示、借书、归还、检索
借阅统计中心：借阅数量、逾期数量、热门图书 TOP10
八、项目亮点
功能完整，覆盖图书管理全流程
借阅统计模块突出，适合课程设计重点展示
界面美观、交互友好
代码结构清晰，注释完善
可直接运行、可演示、可写论文
扩展性强，可继续升级权限、报表、图表等功能
九、版本信息
版本：v2.0.7状态：已完成、可正常运行开发时间：2025开发团队：永无 Bug 队
十、声明
本项目仅用于学习、课程设计、毕业设计交流。禁止用于商业用途。使用请注明来源：永无 Bug 队。
