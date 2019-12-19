# 获取源码
http://sourceforge.net/projects/cunit/
# 获取帮助文档
http://cunit.sourceforge.net/doc/index.html
# 编译前准备
解压下载的压缩包，阅读README和INSTALL文件
确认安装了libtool库
# 编译CUnit
## 1. 运行autoconf 生成configure文件
## 2. 如果遇到configure: error: cannot find install-sh or install.sh in . ./.. ./../..
  在Cunit的根目录下执行autoreconf -f -i -Wall,no-obsolete
## 3. 修改Cunit根目录下的config.sub,在下面三处地方加入要使用的架构：
1）
\# Here we handle the default operating systems that come with various machines.  
\# The value should be what the vendor currently ships out the door with their  
\# machine or put another way, the most popular os provided with the machine.  

\# Note that if you're going to try to match "-MANUFACTURER" here (say,  
\# "-sun"), then you have to tell the case statement up towards the top  
\# that MANUFACTURER isn't an operating system.  Otherwise, code above  
\# will signal an error saying that MANUFACTURER isn't an operating  
\# system, and we'll never get to this point.  

case $basic_machine in
    score-*)
        os=-elf
        ;;
    spu-*)
        os=-elf
        ;;
    csky*-)
        os=-elf
        ;;
    *-acorn)
        os=-riscix1.2
        ;;
    arm*-rebel)
        os=-linux
        ;;
    arm*-semi)
        os=-aout
        ;;
    c4x-* | tic4x-*)
        os=-coff
        ;;
    c8051-*)
        os=-elf
        ;;
2）
# Decode aliases for certain CPU-COMPANY combinations.
case $basic_machine in
    # Recognize the basic CPU types without company name.
    # Some are omitted here because they have special meanings below.
    1750a | 580 \
    | a29k \
    | aarch64 | aarch64_be \
    | alpha | alphaev[4-8] | alphaev56 | alphaev6[78] | alphapca5[67] \
    | alpha64 | alpha64ev[4-8] | alpha64ev56 | alpha64ev6[78] | alpha64pca5[67] \
    | am33_2.0 \
    | arc | arceb \
    | arm | arm[bl]e | arme[lb] | armv[2-8] | armv[3-8][lb] | armv7[arm] \
    | avr | avr32 \
    | ba \
    | be32 | be64 \
    | bfin \
    | c4x | c8051 | clipper \
    | d10v | d30v | dlx | dsp16xx \
    | e2k | epiphany \
    | fido | fr30 | frv | ft32 \
    | h8300 | h8500 | hppa | hppa1.[01] | hppa2.0 | hppa2.0[nw] | hppa64 \
    | hexagon \
    | i370 | i860 | i960 | ia64 \
    | ip2k | iq2000 \
    | k1om \
    | le32 | le64 \
    | lm32 \
    | csky \
    | m32c | m32r | m32rle | m68000 | m68k | m88k \

3）
# We use `pc' rather than `unknown'
    # because (1) that's what they normally are, and
    # (2) the word "unknown" tends to confuse beginning users.
    i*86 | x86_64)
      basic_machine=$basic_machine-pc
      ;;
    # Object if more than one company name word.
    *-*-*)
        echo Invalid configuration \`$1\': machine \`$basic_machine\' not recognized 1>&2
        exit 1
        ;;
    # Recognize the basic CPU types with company name.
    580-* \
    | a29k-* \
    | aarch64-* | aarch64_be-* \
    | alpha-* | alphaev[4-8]-* | alphaev56-* | alphaev6[78]-* \
    | alpha64-* | alpha64ev[4-8]-* | alpha64ev56-* | alpha64ev6[78]-* \
    | alphapca5[67]-* | alpha64pca5[67]-* | arc-* | arceb-* \
    | arm-*  | armbe-* | armle-* | armeb-* | armv*-* \
    | avr-* | avr32-* \
    | ba-* \
    | csky-* \
    | be32-* | be64-* \
    | bfin-* | bs2000-* \
    | c[123]* | c30-* | [cjt]90-* | c4x-* \
    
    ## 4. 运行configure文件生成Makefile
    CC="csky-abiv2-elf-gcc" CFLAGS="--static" ./configure --host=csky --build=x86_64  --prefix=./install
    
    ## 5. 编译
    make
    make install
