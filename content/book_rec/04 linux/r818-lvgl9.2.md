```
[LVGL-v9.2移植 | 东山Π](https://dshanpi.100ask.net/docs/T113i-Industrial/part4/LVGL-v9.2Porting/)

```
### 1. 下载lvgl
```
git clone https://github.com/lvgl/lv_port_linux.git  
cd lv_port_linux/  
git submodule update --init --recursive
```
查看目录结构：
```
pi@pi-T:~/lv_port_linux$ tree -L 2
.
├── boards
│   ├── f-and-s_picocoremx93
│   ├── glyn_ui2-starter-kit
│   ├── nxp_imx93
│   ├── renesas_rz-g3e-evkit
│   ├── stm32mp157f-dk
│   ├── texas-instruments_sk-am62b-p1
│   ├── texas-instruments_sk-am62l
│   ├── texas-instruments_sk-am62p-lp
│   ├── toradex-verdin_am62
│   └── toradex-verdin_imx8m-mini
├── CMakeLists.txt
├── configs
│   ├── drm-egl-2d.defaults
│   ├── drm-egl-3d.defaults
│   ├── fbdev.defaults
│   ├── glfw-3d.defaults
│   ├── glfw.defaults
│   ├── sdl.defaults
│   ├── template
│   ├── wayland.defaults
│   ├── wayland-egl.defaults
│   └── wayland-g2d.defaults
├── docker
│   ├── Dockerfile_cross
│   └── Dockerfile_DEBIAN
├── example
│   ├── CMakeLists.txt
│   └── main.c
├── LICENSE
├── lv_conf.defaults
├── lv_conf.defconfig
├── lvgl
│   ├── CMakeLists.txt
│   ├── CMakePresets.json
│   ├── component.mk
│   ├── configs
│   ├── COPYRIGHTS.md
│   ├── demos
│   ├── docs
│   ├── env_support
│   ├── examples
│   ├── idf_component.yml
│   ├── Kconfig
│   ├── library.json
│   ├── library.properties
│   ├── libs
│   ├── LICENCE.txt
│   ├── lv_conf_template.h
│   ├── lvgl.h
│   ├── lvgl.mk
│   ├── lvgl.pc.in
│   ├── lvgl_private.h
│   ├── lv_version.h
│   ├── lv_version.h.in
│   ├── README.md
│   ├── SConscript
│   ├── scripts
│   ├── src
│   ├── tests
│   └── zephyr
├── manifest.json
├── README.md
├── src
│   ├── lib
│   └── main.c
└── user_cross_compile_setup.cmake

28 directories, 39 files
```


### 交叉编译准备

交叉编译工具链的位置
```
/home/pi/r818/DshanPI-ROSx-TinaSDK-V1/prebuilt/gcc/linux-x86/aarch64/toolchain-sunxi-glibc/toolchain
```

```
adb devices

adb push D:/vmware/img/main /mnt/UDISK/

adb shell chmod +x /mnt/UDISK/main

```


```
                compatible = "focaltech,fts";

                reg = <0x38>;

                status = "okay";

                interrupt-parent = <&pio>;

                interrupts = <PH 12 IRQ_TYPE_LEVEL_LOW>;

                focaltech,reset-gpio = <&pio PH 11 GPIO_ACTIVE_HIGH>;

                focaltech,irq-gpio = <&pio PH 12 IRQ_TYPE_LEVEL_LOW>;

                focaltech,max-touch-number = <5>;

                    //focaltech,display-coords = <0 0 800 480>;

                focaltech,display-coords = <0 0 480 800>;

                    focaltech,reg_vdd = <0x0000001f>;

                    focaltech,reg_avdd = <0x0000001f>;

                //focaltech,reg_vdd = <&reg_3v3>;

                //focaltech,reg_avdd = <&reg_3v3>;
                
```