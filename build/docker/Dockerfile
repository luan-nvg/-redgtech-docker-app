# define a imagem base
FROM ubuntu:latest
# define o mantenedor da imagem
LABEL maintainer="luan-nvg"
# COPY ../../redgtech-onesignal /redgtech-onesignal

# COPY /dev/bus/usb:/dev/bus/usb
WORKDIR /Projects/redgtech-app
# Atualiza a imagem com os pacotes
EXPOSE 8082
RUN apt-get update && apt-get install -y --no-install-recommends apt-utils
RUN apt-get install -y android-sdk
RUN apt-get install -y tzdata
RUN apt-get install -y wget
RUN apt-get install -y unzip
RUN apt-get install -y npm
RUN apt-get install -y libqt5widgets5
#RUN apt-get install -y openjdk-8-jdk 
RUN apt-get install -y git-all
RUN apt-get install -y lsof
RUN npm install -g react-native-cli
RUN set your timezone
RUN ln -fs /usr/share/zoneinfo/America/New_York /etc/localtime
RUN dpkg-reconfigure --frontend noninteractive tzdata
RUN ls -l
RUN mkdir /usr/lib/android-sdk/cmdline-tools
RUN cd /usr/lib/android-sdk/cmdline-tools && wget https://dl.google.com/android/repository/commandlinetools-linux-6514223_latest.zip
RUN cd /usr/lib/android-sdk/cmdline-tools/ && unzip commandlinetools-linux-6514223_latest.zip
RUN cd /usr/lib/android-sdk/cmdline-tools/tools/bin && yes | ./sdkmanager --licenses --sdk_root=${ANDROID_HOME}
RUN touch /root/.android/repositories.cfg
# Platform tools
RUN cd /usr/lib/android-sdk/cmdline-tools/tools/bin && ./sdkmanager "emulator" "tools" "platform-tools"
#openjdk-8-jdk coloquei agr para testar
# Please keep all sections in descending order!
RUN cd /usr/lib/android-sdk/cmdline-tools/tools/bin &&  yes | ./sdkmanager \
    "platforms;android-29" \
    "platforms;android-28" \
    "platforms;android-27" \
    "platforms;android-26" \
    "platforms;android-25" \
    "platforms;android-24" \
    "platforms;android-23" \
    "platforms;android-22" \
    "platforms;android-21" \
    "platforms;android-19" \
    "platforms;android-17" \
    "platforms;android-15" \
    "build-tools;29.0.3" \
    "build-tools;29.0.2" \
    "build-tools;29.0.1" \
    "build-tools;29.0.0" \
    "build-tools;28.0.3" \
    "build-tools;28.0.2" \
    "build-tools;28.0.1" \
    "build-tools;28.0.0" \
    "build-tools;27.0.3" \
    "build-tools;27.0.2" \
    "build-tools;27.0.1" \
    "build-tools;27.0.0" \
    "build-tools;26.0.2" \
    "build-tools;26.0.1" \
    "build-tools;25.0.3" \
    "build-tools;24.0.3" \
    "build-tools;23.0.3" \
    "build-tools;22.0.1" \
    "build-tools;21.1.2" \
    "build-tools;19.1.0" \
    "build-tools;17.0.0" \
    "system-images;android-29;google_apis;x86" \
    "system-images;android-28;google_apis;x86_64" \
    "system-images;android-26;google_apis;x86" \
    "system-images;android-25;google_apis;armeabi-v7a" \
    "system-images;android-24;default;armeabi-v7a" \
    "system-images;android-22;default;armeabi-v7a" \
    "system-images;android-19;default;armeabi-v7a" \
    "extras;android;m2repository" \
    "extras;google;m2repository" \
    "extras;google;google_play_services" \
    "extras;m2repository;com;android;support;constraint;constraint-layout;1.0.2" \
    "extras;m2repository;com;android;support;constraint;constraint-layout;1.0.1" \
    "add-ons;addon-google_apis-google-23" \
    "add-ons;addon-google_apis-google-22" \
    "add-ons;addon-google_apis-google-21"

# Gradle PPA
ENV GRADLE_VERSION=5.4.1
ENV PATH=$PATH:"/opt/gradle/gradle-5.4.1/bin/"
RUN wget https://services.gradle.org/distributions/gradle-${GRADLE_VERSION}-bin.zip -P /tmp \
    && unzip -d /opt/gradle /tmp/gradle-*.zip \
    && chmod +775 /opt/gradle \
    && gradle --version \
    && rm -rf /tmp/gradle*
# SDKs
# Please keep these in descending order!
# The `yes` is for accepting all non-standard tool licenses.

#RUN cd /usr/lib/android-sdk/cmdline-tools/tools/bin && yes | ./sdkmanager --update --channel=3
# Please keep all sections in descending order!
#RUN cd /usr/lib/android-sdk/cmdline-tools/tools/bin && ./sdkmanager "platforms;android-28"

#ENTRYPOINT [ "sh","/start.server.sh" ]

