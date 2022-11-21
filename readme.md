# Introduction
Mini OS

Step by step learning to create an OS

## 常用命令

更新 mini-os
```
cargo build --release
```

生成镜像
```
rust-objcopy --strip-all target/riscv64gc-unknown-none-elf/release/mini-os -O binary target/riscv64gc-unknown-none-elf/release/mini-os.bin
```

启动 qemu
```
qemu-system-riscv64
-machine virt
-nographic
-bios ./bootloader/rustsbi-qemu.bin
-device loader,file=target/riscv64gc-unknown-none-elf/release/mini-os.bin,addr=0x80200000
-s -S
```

启动 GDB 调试
```
riscv64-unknown-elf-gdb \
    -ex 'file target/riscv64gc-unknown-none-elf/release/mini-os' \
    -ex 'set arch riscv:rv64' \
    -ex 'target remote localhost:1234'
```
## Target


<!-- ### 虚拟化
KVM

使用 Intel VT-x 技术实现 CPU 虚拟化
使用 EPT 技术实现内存虚拟化
支持虚拟 x86 实模式运行环境
支持虚拟 CPUID 指令
支持虚拟 HLT 指令，Guest 利用 HLT 指令关机 -->

## Reference

* http://rcore-os.cn/rCore-Tutorial-Book-v3/chapter1/1app-ee-platform.html
    * https://github.com/rcore-os/rCore-Tutorial-v3/tree/ch1
* https://github.com/phil-opp/blog_os