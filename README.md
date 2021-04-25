# PCRAutoTimeline

代码基于GPLv3开源，仅供学习交流，禁止用于商业用途

公主连结帧精度自动打轴(原理读取模拟器内存，时间识别误差在0.1ms以下，但是由于模拟器延迟，可能会有±1帧的误差)  
仅适配x64模拟器  
目前仅实现了实时帧数(逻辑帧)获取功能  
感谢[QTRHacker](https://github.com/ZQiu233/QTRHacker)提供的内存搜索功能(AobscanHelper)

## 用法

### 编写timeline.txt

格式:
```
帧校准 时间校准
<技能释放条件> <站位>
<技能释放条件> <站位>
...
```

如:
```
5 0.0
f1000 4
f1500 2
f1600 1
t10.34 3
```

技能释放条件有两种：
1. 根据小数时间,`t2.4`代表剩余2.4s释放
2. 根据内部帧数(不是摸轴器的帧数，中间差ub的时间计数),`f1000`代表1000帧时释放

站位为1-5的数字

### 依赖

项目依赖于.net 5.0 runtime，请自行百度

### 校准

校准代表着模拟器处理造成的延迟，一般会保持不变，技能释放时，如果打开技能动画，帧数会暂停，你可以根据暂停时候的值和预期值做出帧数的校准

### 运行程序

1. 必须使用管理员模式运行，先进入会战（模拟战也可），然后在开始时暂停
2. 先进行五个站位的鼠标位置的校准，从1-5，将鼠标移至对应位置然后在窗口按回车即可
3. 输入模拟器主程序的PID(不要输错成前台ui程序)
4. 等待扫描，结束后会显示当前帧数和剩余时间
5. 继续模拟器即可
6. 继续运行后不要乱动鼠标！！！

