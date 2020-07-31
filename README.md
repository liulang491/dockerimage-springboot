# dockerimage-springboot

#### 拉取地址

* registry.cn-shanghai.aliyuncs.com/yingzhuo/springboot:8
* registry.cn-shanghai.aliyuncs.com/yingzhuo/springboot:11

#### 用法

```dockerfile
# ----------------------------------------------------------------------------------
# 预构建阶段
# ----------------------------------------------------------------------------------
FROM registry.cn-shanghai.aliyuncs.com/yingzhuo/springboot:8 as builder
WORKDIR /tmp
COPY ./*.jar app.jar

# 解压缩并删除无用依赖和无用文件
RUN java -Djarmode=layertools -jar /tmp/app.jar extract && \
    rm -rf /tmp/dependencies/BOOT-INF/lib/spring-boot-jarmode-layertools-*.jar && \
    rm -rf /tmp/application/BOOT-INF/classpath.idx && \
    rm -rf /tmp/application/BOOT-INF/layers.idx

# ----------------------------------------------------------------------------------
# 实际构建阶段
# ----------------------------------------------------------------------------------
FROM registry.cn-shanghai.aliyuncs.com/yingzhuo/springboot:8

# 分层拷贝
COPY --from=builder /tmp/dependencies/ ./
COPY --from=builder /tmp/spring-boot-loader/ ./
COPY --from=builder /tmp/snapshot-dependencies/ ./
COPY --from=builder /tmp/application/ ./

# 预设环境变量
ENV APP_PROFILES=k8s

# 暴露端口 (Optional)
EXPOSE 8080
```

#### 注意

* 本镜像基于OpenJDK