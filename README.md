重新编译解决android30崩溃问题，编好的包自取在build_output路径下 参考了(https://github.com/alanwang4523/ijkplayer_Build4Android.git)
增加mp3和https 支持 

如需编译其他格式，请自行修改。
本人编译环境
系统：MacOS，Apple M1
NDK: android-ndk-r10e


M1芯片报错 ERROR: Unknown host CPU architecture: arm64 需要修改 
文件路径：/Users/xxx/env/android-sdk/ndk/android-ndk-r10e/ndk-build

`HOST_ARCH=$(uname -m)`
`case $HOST_ARCH in`
    `i?86) HOST_ARCH=x86;;`
    `x86_64|amd64) HOST_ARCH=x86_64;;`
    `*) echo "ERROR: Unknown host CPU architecture: $HOST_ARCH"`
       `exit 1`
`esac`
`log "HOST_ARCH=$HOST_ARCH"`

把 x86_64|amd64) 这里加一个，改成 x86_64|amd64|arm64)

编译 ijkplayer 出错，错误如下：
**Android NDK: Host 'awk' tool is outdated. Please define NDK_HOST_AWK to point to Gawk or Nawk !**

**解决方案：[参考链接](https://stackoverflow.com/questions/8384213/android-ndk-revision-7-host-awk-tool-is-outdated-error)**

```bash
1、进入到目录： android-ndk-r10e/prebuilt/darwin-x86_64/bin
2、将 awk 重命名为 awk_
```

其他可按项目现成文件编译即可
