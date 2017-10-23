## Docker

在　SpringBoot 项目中使用　docker

Dockerfile

> FROM openjdk:8
ADD targets/*.jar /app.jar
ENTRYPOINT ["java", "-jar", "/app.jar"]


构建镜像：　docker build -f Dockerfile -t spring-boot-app .

运行：　docker run -p 8080:8080 spring-boot-app


## docker push 

使用　docker push 上传镜像到　ｄocker hub　上

－　docker login

    输入用户名和密码
    
－　docker tag hello-world splade/hello-world:0.0.1

- docker push splade/hello-world:0.0.1

> 注意: push 的镜像需要唯一知己的账号下面，即，　`splade/docker-image-name:tag`
否则， 会出现权限错误