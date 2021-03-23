FROM ubuntu:20.04
LABEL author=benjyair site=https://www.benjyair.com/


# 准备环境与工具链
RUN apt-get update \
    && apt-get install sudo -y \
    && sudo apt-get install curl unzip -y \
    && sudo apt-get install build-essential file apt-utils -y

ENV JAVA_URL="https://code.aliyun.com/kar/oracle-jdk/raw/3c932f02aa11e79dc39e4a68f5b0483ec1d32abe/jdk-8u251-linux-x64.tar.gz" \
    JAVA_VERSION="jdk1.8.0_251" \
    GRADLE_URL="https://downloads.gradle.org/distributions/gradle-6.7-bin.zip" \
    GRADLE_VERSION="gradle-6.7" \
    SDK_URL="https://dl.google.com/android/repository/sdk-tools-linux-3859397.zip" \
    ANDROID_SDK_ROOT="/usr/local/android-sdk" \
    ANDROID_VERSION=30 \
    ANDROID_BUILD_TOOLS_VERSION=30.0.2


# 安装 Java 8
RUN mkdir /usr/local/java \
    && cd /usr/local/java \
    && curl -o "$JAVA_VERSION.tar.gz" $JAVA_URL \
    && tar -zxvf "$JAVA_VERSION.tar.gz" \
    && rm "$JAVA_VERSION.tar.gz"

ENV JAVA_HOME="/usr/local/java/$JAVA_VERSION" \
    JRE_HOME="/usr/local/java/$JAVA_VERSION/jre"

ENV CLASSPATH=$JAVA_HOME/lib:$JAVA_HOME/jre/lib \
    PATH="${PATH}:${JAVA_HOME}/bin:${JRE_HOME}/bin"


# 安装 Android SDK
RUN mkdir -p ~/.android \
    && touch ~/.android/repositories.cfg \
    && mkdir "$ANDROID_SDK_ROOT" .android \
    && cd "$ANDROID_SDK_ROOT" \
    && curl -o sdk.zip $SDK_URL \
    && unzip sdk.zip \
    && rm sdk.zip \
    && mkdir "$ANDROID_SDK_ROOT/licenses" || true \
    && echo "24333f8a63b6825ea9c5514f83c2829b004d1fee" > "$ANDROID_SDK_ROOT/licenses/android-sdk-license" \
    && $ANDROID_SDK_ROOT/tools/bin/sdkmanager --update \
    && $ANDROID_SDK_ROOT/tools/bin/sdkmanager "build-tools;${ANDROID_BUILD_TOOLS_VERSION}" \
    "platforms;android-${ANDROID_VERSION}" \
    "platform-tools"

ENV PATH="${PATH}:${ANDROID_SDK_ROOT}/tools:${ANDROID_SDK_ROOT}/platform-tools"


# # 安装 Android NDK
# RUN curl http://dl.google.com/android/ndk/android-ndk-r10e-linux-x86_64.bin    && \
#     chmod a+x android-ndk-r10e-linux-x86_64.bin                                && \
#     ./android-ndk-r10e-linux-x86_64.bin -o/usr/local                           && \
#     rm android-ndk-r10e-linux-x86_64.bin
# # 配置 Android NDK 环境变量
# ENV NDK_HOME /usr/local/android-ndk-r10e
# ENV PATH $PATH:$NDK_HOME


# 安装 Gradle，加速编译 APK 过程，也可以使用项目内的 Gradle Wrapper 自动下载当前项目的需要的 Gradle 版本
RUN mkdir /usr/local/gradle \
    && cd /usr/local/gradle \
    && curl -o "$GRADLE_VERSION.zip" $GRADLE_URL \
    && unzip "$GRADLE_VERSION.zip" \
    && rm "$GRADLE_VERSION.zip"

ENV GRADLE_HOME="/usr/local/gradle/$GRADLE_VERSION"
ENV PATH="${PATH}:${GRADLE_HOME}/bin"

# 卸载工具包
RUN sudo apt-get autoremove curl unzip -y

# docker build -t benjyair/android-env .
# docker push benjyair/android-env
