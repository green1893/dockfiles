FROM centos:7.6.1810
MAINTAINER zhaozhiwu@zrar.com
ENV TZ=Asia/Shanghai\
    LANG=zh_CN.UTF-8\
    LANGUAGE=zh_CN:zh\
    LC_ALL=zh_CN.UTF-8
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime \
&& echo $TZ > /etc/timezone \
&& yum install glibc-common java-1.8.0-openjdk -y &&
&& localedef -c -f UTF-8 -i zh_CN zh_CN.utf8
ENV JAVA_HOME=/usr/lib/jvm/java-1.8-openjdk/jre \
    PATH=$PATH:/usr/lib/jvm/java-1.8-openjdk/jre/bin:/usr/lib/jvm/java-1.8-openjdk/bin
RUN rm -rf /tmp/*\
&& rm -rf /var/cache/yum/*