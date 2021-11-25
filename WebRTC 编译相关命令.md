# WebRTC 编译相关命令

设置boto文件路劲

```shell
export NO_AUTH_BOTO_CONFIG=/home/side/.boto
```

设置depot_tools环境变量

```shell
export PATH=/home/side/Documents/own-webrtc/depot_tools:$PATH
```

生成 ninja 构建文件

```shell
gn gen out/linux_debug_x64/ --args='target_os="linux" target_cpu="x64" is_debug=true'
```

编译 WebRTC

```shell
ninja -C out/linux_release_x64/ webrtc
```

提取头文件

```shell
cd src
rm ~/Downloads/webrtc-lib/include && \
mkdir -p ~/Downloads/webrtc-lib/include && \
find . -maxdepth 1 -name "*.h" -exec cp --parents '{}' ~/Downloads/webrtc-lib/include ';' && \
find api audio base call common_audio common_video \
	logging media modules p2p pc rtc_base rtc_tools \
	sdk stats system_wrappers third_party/abseil-cpp \
	video third_party/abseil-cpp -name "*.h" \
	-exec cp --parents '{}' ~/Downloads/webrtc-lib/include ';'
```



