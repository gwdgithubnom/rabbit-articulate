# 查询maven版本

```bash

mvn org.apache.maven.plugins:maven-help-plugin:2.1.1:evaluate -Dexpression=project.version | grep -v '\['
mvn org.apache.maven.plugins:maven-help-plugin:2.1.1:evaluate -Dexpression=project.version |sed -n -e '/^\[.*\]/ !{ /^[0-9]/ { p; q } }'
mvn org.apache.maven.plugins:maven-help-plugin:3.2.0:evaluate -Dexpression=project.version -q -DforceStdout

```
# 脚本获取部署的环境
```bash
export projectVersion=`mvn org.apache.maven.plugins:maven-help-plugin:3.2.0:evaluate -Dexpression=project.version -q -DforceStdout`
export projectArtifactId=`mvn org.apache.maven.plugins:maven-help-plugin:3.2.0:evaluate -Dexpression=project.artifactId -q -DforceStdout`
export snapshortName=$projectArtifactId"-"$projectVersion
export depsName=$snapshortName"-deps.jar"
export targetName=$snapshortName".jar"
export branchName=`git branch|grep \*|awk -F' ' '{print $2}'`
```
