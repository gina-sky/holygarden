 - 修改背光引脚pwm2，屏名称 .name = "ili9881c_dsi_panel"
 - 复位引脚pb8

```
https://dshanpi.100ask.net/docs/T113i-Industrial/part4/LVGL-v9.2Porting/
hexdump /dev/input/event3
```

```
                        ctp@5d {
                                compatible = "goodix,gt911";
                                reg = <0x5d>;
                                status = "okay";
                                interrupt-parent = <&pio>;
                                interrupts = <PD 12 IRQ_TYPE_EDGE_FALLING>; // GT911 EDGE_FALLING
                                goodix,irq-gpio = <&pio PD 12 GPIO_ACTIVE_HIGH>;
                                goodix,reset-gpio = <&pio PD 11 GPIO_ACTIVE_HIGH>;
                                goodix,max-touch-number = <5>;
                                goodix,display-coords = <0 0 800 1280>;
                                goodix,reg_vdd = <0x0000001f>;
                                goodix,reg_avdd = <0x0000001f>;
                        };



	
                        

```

```
	ctp@5d {
		compatible = "allwinner,goodix";
		device_type = "ctp";
		reg = <0x5d>;
		status = "okay";
		ctp_name = "gt9xxnew_ts";
		ctp_twi_id = <0x0>;
		ctp_twi_addr = <0x5d>;
		ctp_screen_max_x = <800>;
		ctp_screen_max_y = <1280>;
		ctp_revert_x_flag = <0x0>;
		ctp_revert_y_flag = <0x0>;
		ctp_exchange_x_y_flag = <0x0>;
		ctp_int_port = <&pio PD 12 GPIO_ACTIVE_HIGH>;
		ctp_wakeup = <&pio PD 11 GPIO_ACTIVE_HIGH>;
	};
```


```
→ Device Drivers → Input device support → Touchscreens -> gt9xx
```

```
find ./ -name "sun50iw10p1_tina_defconfig"
```


```
ctp@14 { 
		status = "okay"; 
		ctp_used = <1>; 
		ctp_name = "gt9xxnew"; 
		ctp_twi_id = <0x0>; 
		ctp_twi_addr = <0x14>; 
		ctp_screen_max_x = <800>; 
		ctp_screen_max_y = <1280>; 
		ctp_revert_x_flag = <0x0>; 
		ctp_revert_y_flag = <0x1>; 
		ctp_exchange_x_y_flag = <0x0>; 
		ctp_int_port = <&pio PD 12 6 1 3 0xffffffff>; 
		ctp_wakeup = <&pio PD 11 1 1 3 0xffffffff>; 
		};
```