WebRTC
=================

# �ٷ�ָ�� [webrtc native development]( http://www.webrtc.org/native-code/development )
# SkywaySDK
Skyway��docomo�ṩ��һ��sdk����������webRTC��һ����װ�������Ͽ�website�Ľ���ûɶ����
Skyway�Ļ�����Ϣ�����������ǵĹ����Ͽ�����
http://nttcom.github.io/skyway/en/docs/#Android
SkywaySDKʹ�õ�lib���Բο����µ�website��
https://webrtc.org/native-code/android/
ͨ���������build script��ȡ�����µİ汾��
https://github.com/pristineio/webrtc-build-scripts
����ͨ�����룬����skyway��Android Framework�ĵ��ù�ϵ��
# webrtc��̬������
�ο�[gyp](gyp.md)
##  ������װ
### ���ع���Depot Tools
http://dev.chromium.org/developers/how-tos/install-depot-tools
> git clone https://chromium.googlesource.com/chromium/tools/depot_tools.git ~/bin/
> export PATH=~/bin/depot_tools:$PATH
> source ~/.bashrc
### Դ����
���ն��л�����Ҫ���ش����workspace,ִ��
> mkdir webrtc-checkout
> cd webrtc-checkout
> fetch webrtc_android
�������ʧ��,����ʹ�ô������VPN�ȷ������������������17G��
### ����
����������ܶ๤�߰�,ִ������Ľű�,��������ȱʧ�Ĺ���:
> ./build/install-build-deps.sh
����Android SDK��NDK,���ع�����,���»�������:
��/etc/profile�ļ�������(��ʵ��Ŀ¼Ϊ׼,���ο�):
export JAVA_HOME="/usr/lib/jvm/java-7-openjdk-amd64"
export ANDROID_NDK_ROOT="/home/user/Android/android-ndk-r10e"
export ANDROID_SDK_ROOT="/home/user/Android/Sdk"
export PATH="$PATH:$JAVA_HOME/bin:$JAVA_HOME/jre/bin"
export PATH="$PATH:$ANDROID_SDK_ROOT/platform-tools/:$ANDROID_SDK_ROOT/tools"
export PATH="$PATH:$ANDROID_NDK_ROOT/prebuilt/linux-x86_64/bin"
export CLASSPATH="$CLASSPATH:.:$JAVA_HOME/lib:$JAVA_HOME/jre/lib"
��.bashrc�����ļ�������:
export GYP_DEFINES="OS=android"
��������ִ��source��ʹ����Ч��
### ����
�л���srcĿ¼,�״ν���ȫ����,ִ��
> ninja -C out/Debug/
����ʱ,���յ�ɾ�������ظ�����Ľ���,����˵��ִ��(���״�����)
> python setup_links.py
�Ժ������Ҫ����ĳ��ģ��,��AppRTC,����ִ��:
> ninja -C out/Debug/ AppRTCDemo
ÿ�α���ǰ,��Ҫִ��> gclient runhooks
*���������������ʺϵ�ǰ����ƽ̨�ı��빤�̺ͽű�*
����,���������������������ִ��
> gclient sync
*���������ͬ�����´���,����ͬʱ��hooks,��ʱ�ϳ�*
##  ����ģ��
### WebRTC Engine Demo
λ��:src/webrtc/examples/android/media_demo
ģ��:org.webrtc.webrtcdemo
��ģ�����ڲ���RTC�Ľ���,��Ŀǰ����������,�޷���ͨ��
### AppRTC Demo
λ��:src/webrtc/examples/androidapp
ģ��:org.appspot.apprtc
��app����ͨ��Ĭ�ϵ�room server:[apprtc]( https://apprtc.appspot.com )������room,�ֻ��˿������뷿���,���������������Ƶ��
����
####  ��������
1. �������[apprtc]( https://apprtc.appspot.com ),����һ�������,Ҳ�����������;
2. �ֻ��˴�AppRTC,��room name������ղŵķ����;
3. ���OK,��Room names�б���,�����Ҫ���ӵķ����,Ȼ��������ͼ��;
4. ���ӳɹ�,����������Ͽ����ֻ���camera��ʵʱԤ��,����������Ƶ���䡣
