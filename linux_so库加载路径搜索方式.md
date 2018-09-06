【出自《Linux C编程一站式学习》346页】

共享库的搜索路径由动态链接器决定，从ld.so(8)的Man Page可以查到共享库路径的搜索顺序：

1. 首先在环境变量LD_LIBRARY_PATH所记录的路径中查找。
2. 然后在缓存文件/etc/ld.so.cache中查找。这个缓存文件由ldconfig命令读取配置文件/etc/ls.so.conf之后生成。
3. 如果上述步骤都找不到，则到默认的系统路径中查找，先是/usr/lib然后是/lib。




