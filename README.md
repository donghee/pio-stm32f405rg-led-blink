
### pio debug

platformio 에서 디버깅 하는방법. 그러나 pio 쉘에서 gdb에서Ctrl-C (SIGINT) 가 작동 안한다.

```
pio debug --interface=gdb -- -x .pioinit
```

### gdb 이용하는 방법

JLinkGDB 서버

```
JLinkGDBServer -if SWD -device STM32F405RG
```

.pioinit: gdb 시작 명령
```
file .pio/build/genericSTM32F405RG/firmware.elf
target remote localhost:2331
monitor reset
#monitor flash erase
load
break main
```

gdb로 서버 접속. .pioinit 읽어서 gdb 명령 실행
```
~/.platformio/packages/toolchain-gccarmnoneeabi/bin/arm-none-eabi-gdb -x .pioinit
```

