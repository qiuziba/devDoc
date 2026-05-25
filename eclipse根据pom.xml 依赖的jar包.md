eclipse maven pom.xml 依赖的jar包

1、首先，将maven项目install下

步骤：在maven项目上右键，Run As，Maven install 

2、然后，对maven项目进行build,并copy-dependencies

步骤：在pom.xml文件上右键，Run As,Maven build...

3、接着，在弹出的对话框中的：Goals输入框中输入：dependency:copy-dependencies

4、最后：点击对话框中的：Run

5、获取jar包：对项目刷新，进入：项目下的target/dependency/目录下（获取的jar包都在这里）
