FROM alpine:3.12.0

WORKDIR /opt

COPY ./docker-entrypoint.sh docker-entrypoint.sh

RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g' /etc/apk/repositories && \
    apk add --update bash ca-certificates openjdk11-jre font-adobe-100dpi ttf-dejavu fontconfig && \
    rm -rf /var/cache/apk/* && \
    rm -rf "$JAVA_HOME/man/" && \
    rm -rf "$JAVA_HOME/demo/" && \
    rm -rf "$JAVA_HOME/release" && \
    rm -rf "$JAVA_HOME/THIRD_PARTY_README" && \
    rm -rf "$JAVA_HOME/ASSEMBLY_EXCEPTION" && \
    rm -rf "$JAVA_HOME/LICENSE" && \
    rm -rf "$JAVA_HOME/README" && \
    rm -rf "$JAVA_HOME/jre/ASSEMBLY_EXCEPTION" && \
    rm -rf "$JAVA_HOME/jre/LICENSE" && \
    rm -rf "$JAVA_HOME/jre/THIRD_PARTY_README" && \
    rm -rf "$JAVA_HOME/lib/missioncontrol" && \
    rm -rf "$JAVA_HOME/lib/visualvm" && \
    rm -rf "$JAVA_HOME/lib/*javafx*" && \
    rm -rf "$JAVA_HOME/jre/lib/plugin.jar" && \
    rm -rf "$JAVA_HOME/jre/lib/ext/jfxrt.jar" && \
    rm -rf "$JAVA_HOME/jre/bin/javaws" && \
    rm -rf "$JAVA_HOME/jre/lib/javaws.jar" && \
    rm -rf "$JAVA_HOME/jre/lib/desktop" && \
    rm -rf "$JAVA_HOME/jre/plugin" && \
    rm -rf "$JAVA_HOME/jre/lib/deploy*" && \
    rm -rf "$JAVA_HOME/jre/lib/*javafx*" && \
    rm -rf "$JAVA_HOME/jre/lib/*jfx*" && \
    rm -rf "$JAVA_HOME/jre/lib/amd64/libdecora_sse.so" && \
    rm -rf "$JAVA_HOME/jre/lib/amd64/libprism_*.so" && \
    rm -rf "$JAVA_HOME/jre/lib/amd64/libfxplugins.so" && \
    rm -rf "$JAVA_HOME/jre/lib/amd64/libglass.so" && \
    rm -rf "$JAVA_HOME/jre/lib/amd64/libgstreamer-lite.so" && \
    rm -rf "$JAVA_HOME/jre/lib/amd64/libjavafx*.so" && \
    rm -rf "$JAVA_HOME/jre/lib/amd64/libjfx*.so" && \
    chmod +x /opt/docker-entrypoint.sh

ENTRYPOINT ["./docker-entrypoint.sh"]