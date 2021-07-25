Flycast
=======
For 32bit build: 
make -j3 platform="classic_armv8_a35"

For 64bit build: 
export CFLAGS="-march=armv8-a+crc+simd -mtune=cortex-a35 -mcpu=cortex-a35 -O3 -pipe -fno-plt -fdata-sections -ffunction-sections -Wl,--gc-sections -fno-stack-protector -fno-ident -fomit-frame-pointer -fmerge-all-constants -fno-math-errno -Wl,--gc-sections -falign-functions=1 -falign-jumps=1 -falign-loops=1 -fno-unwind-tables -fno-asynchronous-unwind-tables -fno-unroll-loops -fmerge-all-constants -frename-registers -funsafe-math-optimizations -ftree-vectorize -DHOST_CPU=0x20000006 -DTARGET_LINUX_ARMv8 -DNO_ASM -DARM_ASM -frename-registers -ftree-vectorize -g"
make -j3 WITH_DYNAREC=arm64 HAVE_OPENMP=1 FORCE_GLES=1

MGBA (64 bit)
====
make -j${nproc} platform="goadvance"

FBNEO (64 bit)
======
make -j$(nproc) -C ./src/burner/libretro generate-files
make -C ./src/burner/libretro profile=performance

PCSX-REARMED (32 bit)
===========
export CFLAGS="$CFLAGS -Ofast -Wl,--gc-sections -fno-stack-protector -fno-ident -fomit-frame-pointer -falign-functions=1 -falign-jumps=1 -falign-loops=1 -fno-unwind-tables -fno-asynchronous-unwind-tables -fno-unroll-loops -fmerge-all-constants -fno-math-errno"
make -f Makefile.libretro HAVE_NEON=1 ARCH=arm BUILTIN_GPU=neon DYNAREC=ari64 platform=rpi3 -j$(nproc)

PARALLEL-N64 (32 bit)
============
export CPUFLAGS="-DNO_ASM -DARM -DARM_ASM -DDONT_WANT_ARM_OPTIMIZATIONS -DARM_FIX -DCLASSIC -DARM64 -march=armv8-a+crc -mcpu=cortex-a35 -mtune=cortex-a35 -O3 -fno-tree-vectorize -D__NEON_OPT"
make -j3 WITH_DYNAREC=aarch64  
