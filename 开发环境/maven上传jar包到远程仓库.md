

# maven上传jar包到远程仓库

通常允许上传的远程仓库有两种：Snapshots和Releases，分别为快照版仓库和稳定版仓库。  快照版仓库用于存放不稳定的开发包，稳定版仓库用于存放稳定的包。  

## 通过Nexus UI 界面部署



## 通过Maven命令行部署

### maven deploy

https://www.cnblogs.com/pekkle/p/10373506.html

mvn deploy:deploy-file -DgroupId=com.oracle -DartifactId=ojdbc6 -Dversion=11.2.0.4 -Dpackaging=jar -Dfile=d:/ojdbc6.jar -Durl=http://localhost:8080/repository/xx-third/ -DrepositoryId=xx-third

## 参考

https://www.cnblogs.com/pekkle/p/10373506.html