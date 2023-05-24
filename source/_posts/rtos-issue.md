---
title: rtos_issue
date: 2023-05-18 17:11:14
tags: 
	- rtos
	- TI
	- tda4
categories: tech
---

# Backgroud
记录工作中遇到的tda4中的一些问题，以及自己是怎么解决的。  
更多是记录一些玄幻的问题以及原因。

## 加个pintf后一切正常--rtos里面经常发生的
**问题描述：**
在通过控制电源管理芯片20087对摄像头进行上下电过程中，调用写好的写20087寄存器的接口。  
写20087在 rtos内，调用处也在rtos处。  
循环四次上下电四次。  
```
for(camIdx = 0; camIdx < 4; camIdx++){
	// 上电
	powerState.camIndex = camIdx;
	powerState.camState = 1;  // power_on
	appRemoteServiceRun(
	APP_IPC_CPU_MCU2_0,
	APP_REMOTE_SERVICE_CALI_PARAM_NAME,
	APP_REMOTE_SERVICE_SVM_CAM_POWER,
	&powerState,
	sizeof(S_ImoSvmPowerState),
	0);
	appLogWaitMsecs(500);
	// read to judge
	Board_i2c16BitRegRd(i2cHandle, 0x29, 0x0, &reg_v, 1, BOARD_I2C_REG_ADDR_MSB_FIRST, 100);
	if(0x29 != (reg_v>>1)){
	// 出现异常进行断电
		printf("#streamFlag# camIdx = %d cause i2c error!!, reg_v = 0x%x \n", camIdx, reg_v); reg_v = 0xff;
		powerState.camIndex = camIdx;
		powerState.camState = 0;  // power_off
		appRemoteServiceRun(
		APP_IPC_CPU_MCU2_0,
		APP_REMOTE_SERVICE_CALI_PARAM_NAME,
		APP_REMOTE_SERVICE_SVM_CAM_POWER,
		&powerState,
		sizeof(S_ImoSvmPowerState),
		0);
		// printf("#streamFlag# camIdx = %d cause i2c error!!, reg_v = 0x%x \n", camIdx, reg_v); reg_v = 0xff;
	}
}
printf("#streamFlag# test content \n");
```
没有加结尾处的printf后，testcontent 无法打印出来，相当于没走到，加了printf后竟然正常打印testcontent了！

**问题分析:** 
1. 接口appRemoteServiceRun()中加打印跟踪流程  


{% cq %} 学区房是阶级的象征 {% endcq %}