# kernel_samsung_note_20_ultra

## Linux kernel

There are several guides for kernel developers and users. These guides can
be rendered in a number of formats, like HTML and PDF. Please read
Documentation/admin-guide/README.rst first.

In order to build the documentation, use ``make htmldocs`` or
``make pdfdocs``.  The formatted documentation can also be read online at:

https://www.kernel.org/doc/html/latest/

There are various text files in the Documentation/ subdirectory,
several of them using the Restructured Text markup notation.
See Documentation/00-INDEX for a list of what is contained in each file.

Please read the Documentation/process/changes.rst file, as it contains the
requirements for building and running the kernel, and information about
the problems which may result by upgrading your kernel.

### 1. How to Build
        - get Toolchain
                From android git serveru, codesourcery and etc ..
                - gcc/linux-x86/aarch64/aarch64-linux-android-4.9/bin/aarch64-linux-android-

        - make output folder 
                EX) OUTPUT_DIR=out
                $ mkdir out

        - edit Makefile
                edit "CROSS_COMPILE" to right toolchain path(You downloaded).
                        EX)  CROSS_COMPILE=<android platform directory you download>/android/prebuilts/gcc/linux-x86/aarch64/aarch64-linux-android-4.9/bin/aarch64-linux-android-
                        Ex)  CROSS_COMPILE=/usr/local/toolchain/gcc/linux-x86/aarch64/aarch64-linux-android-4.9/bin/aarch64-linux-android- // check the location of toolchain
                edit "REAL_CC" to right toolchain path(You downloaded).
                        EX)  CC=<android platform directory you download>/android/vendor/qcom/proprietary/llvm-arm-toolchain-ship/10.0/bin/clang
                edit "CLANG_TRIPLE" to right path(You downloaded).

        - to Build
                $ export ARCH=arm64
                $ make -C $(pwd) O=$(pwd)/out DTC_EXT=$(pwd)/tools/dtc CONFIG_BUILD_ARM64_DT_OVERLAY=y CLANG_TRIPLE=aarch64-linux-gnu- vendor/c2q_kor_singlew_defconfig
                $ make -C $(pwd) O=$(pwd)/out DTC_EXT=$(pwd)/tools/dtc CONFIG_BUILD_ARM64_DT_OVERLAY=y CLANG_TRIPLE=aarch64-linux-gnu-


### 2. Output files
        - Kernel : arch/arm64/boot/Image
        - module : drivers/*/*.ko

### 3. How to Clean
        Change to OUTPUT_DIR folder
        EX) /home/dpi/qb5_8815/workspace/P4_1716/android/out/target/product/c2q/out
        $ make clean


## 中文

有几个针对内核开发人员和用户的指南。 这些指南可以以多种格式呈现，例如 HTML 和 PDF。 请先阅读 Documentation/admin-guide/README.rst。

要构建文档，请使用 ``make htmldocs`` 或 ``make pdfdocs``。 还可以在线阅读格式化文档：

https://www.kernel.org/doc/html/latest/

Documentation/ 子目录中有各种文本文件，其中一些使用重构文本标记表示法。 有关每个文件中包含的内容的列表，请参阅 Documentation/00-INDEX。

请阅读 Documentation/process/changes.rst 文件，因为它包含构建和运行内核的要求，以及有关升级内核可能导致的问题的信息。

### 1. 如何构建
    - 获取工具链
        从 Android git 服务器、CodeSourcery 等获取...
        - gcc/linux-x86/aarch64/aarch64-linux-android-4.9/bin/aarch64-linux-android-

    - 创建输出文件夹
        例如) OUTPUT_DIR=out
        $ mkdir out

    - 编辑 Makefile
        将 "CROSS_COMPILE" 编辑为正确的工具链路径（您下载的路径）。
        例如) CROSS_COMPILE=<您下载的 Android 平台目录>/android/prebuilts/gcc/linux-x86/aarch64/aarch64-linux-android-4.9/bin/aarch64-linux-android-
        例如) CROSS_COMPILE=/usr/local/toolchain/gcc/linux-x86/aarch64/aarch64-linux-android-4.9/bin/aarch64-linux-android- // 检查工具链的位置
        将 "REAL_CC" 编辑为正确的工具链路径（您下载的路径）。
        例如) CC=<您下载的 Android 平台目录>/android/vendor/qcom/proprietary/llvm-arm-toolchain-ship/10.0/bin/clang
        将 "CLANG_TRIPLE" 编辑为正确的路径（您下载的路径）。

    - 构建
        $ export ARCH=arm64
        $ make -C $(pwd) O=$(pwd)/out DTC_EXT=$(pwd)/tools/dtc CONFIG_BUILD_ARM64_DT_OVERLAY=y CLANG_TRIPLE=aarch64-linux-gnu- vendor/c2q_kor_singlew_defconfig
        $ make -C $(pwd) O=$(pwd)/out DTC_EXT=$(pwd)/tools/dtc CONFIG_BUILD_ARM64_DT_OVERLAY=y CLANG_TRIPLE=aarch64-linux-gnu-


### 2. 输出文件
    - 内核: arch/arm64/boot/Image
    - 模块: drivers/*/*.ko

### 3. 如何清理
    切换到 OUTPUT_DIR 文件夹
    例如) /home/dpi/qb5_8815/workspace/P4_1716/android/out/target/product/c2q/out
    $ make clean