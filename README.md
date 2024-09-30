# ffmpeg_prebuilts
ffmpeg prebuilt libraries used in Bambu Studio

1. Install visual studio 2022; 

2. Insatll msys2: https://repo.msys2.org/distrib/msys2-x86_64-latest.exe; 

3. Modify the "MYSYS2_PATH/mysys2.shell.cmd" file "rem set MSYS2_PATH_TYPE=inherit" to "set MSYS2_PATH_TYPE=inherit"; 

4. Start "X64 Native Tools Command Prompt for VS 2022" and run "MYSYS2_PATH/mysys2.shell.cmd"; 

5. Install pacman tools "pacman -S diffutils make pkg-config yasm" in mysys2 window; 

6. Download ffmpeg source 7.0.2: https://codeload.github.com/FFmpeg/FFmpeg/zip/refs/tags/n7.0.2

7. cd ffmpeg sourece directory in mysys2 shell; 

8. Run command
```
./configure --toolchain=msvc \
--prefix=./dist \
--enable-gpl \
--enable-nonfree \
--enable-shared \
--disable-doc \
--enable-small \
--disable-outdevs \
--disable-filters \
--enable-filter="*null*,afade,*fifo,*format,*resample,aeval,allrgb,allyuv,atempo,pan,*bars,color,*key,crop,draw*,eq*,framerate,*_qsv,*_vaapi,*v4l2*,hw*,scale,volume,test*" \
--disable-protocols \
--enable-protocol=file,fd,pipe,rtp,udp \
--disable-muxers \
--enable-muxer=rtp \
--disable-encoders \
--disable-decoders \
--enable-decoder="*aac*,h264*,mp3*,mjpeg,rv*" \
--disable-demuxers \
--enable-demuxer=h264,mp3,mov \
--disable-zlib \
--disable-avdevice
```

9. Run "make && make install";