# 简介
本项目主要借助 mybatis-generator 为基于 mybatis 的项目生成所需的实体和 DAO。

# 具体操作
1. 先将包含两个 MBG 插件的 mybatis-generator-plugin 项目拉到本地，执行 mvn install 将项目打包并发布到本地 maven 仓库;
2. 修改 generatorConfig.xml 文件，主要是 __jdbcConnection__ 与 __table__ 两个标签;
3. 如果是在 Idea 中打开本项目，可找到 "Maven Projects" 面板，在 "plugins" 中找到 "mybatis-generator:generate",右键点击，选择 Run Maven Build;
4. 步骤3也可在项目根路径执行 maven 命令:
```bash
    mvn mybatis-generator:generate
```
5. 最新版本支持在项目打包时自动生成目标文件;

# 注意事项
1. 在重新生成的时候，Mapper 中的自定义方法会被覆盖;
2. 表中如果有 text 类型的字段，需要自定义 selectByExampleWithBLOBs 方法来针对该字段信息进行查找，或者在生成这张表的相关实体与 DAO 时取消对 BaseMapperGeneratorPlugin 插件的使用;
3. 生成的新文件可能代码格式不符合当前 checkstyle 中规定风格，需要手动修正;