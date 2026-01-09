---
title: Seer2 swf 配置数据表格
date: 2026-01-07 23:16:48
tags: scs
id: scs
---
## id 
### 1.swf
- [1.swf] 
- [56,71,87,111]

### 2.swf
- [1.swf] 
- [25,32,34,60]

### 3.swf
- [1.swf] 
- [62,90,112,204,339]

### 6.swf
- [1.swf] 
- [48,66,79,138,351]

### 8.swf
- [13,19,49,67,165,322]


### 10.swf
- [13,21,35,56,81,134]



### 12.swf
- [15,18,28,59,113]



### 15.swf
- [13,21,35,40,93] [30,36]


### 17.swf
- [17,21,25,42,72] [30,35]


### 19.swf
- [12,16,35,50,76] [30,36]

### 19.swf
- [12,16,35,50,76] [30,36]


### 21.swf
- [10,13,18,26,67] [30,35]



### 24.swf
- [21,35,50,69,102] [30,35]

### 27.swf
- [18,55,66,95,153] [30,35]


### 29.swf
- [46,53,55,63,127] [30,35]


### 31.swf
- [38,54,77,93,150] [30,36]

### 500.swf
- [500.swf] 
- [228,249,284,432]

## 
```rust
# 方式1: 直接编译链接
g++ -o my_app main.cpp -L./lib -larchive_lib -pthread

# 方式2: 使用CMake
cmake_minimum_required(VERSION 3.10)
project(MyApp)

# 添加静态库
add_library(archive_lib STATIC IMPORTED)
set_target_properties(archive_lib PROPERTIES
    IMPORTED_LOCATION "${CMAKE_CURRENT_SOURCE_DIR}/lib/libarchive_lib.a"
)

# 创建可执行文件
add_executable(my_app main.cpp)

# 链接静态库
target_link_libraries(my_app archive_lib pthread)


## 二次构建
```python
# SConstruct (主构建文件)
import os

# 创建构建环境
env = Environment()

# 设置编译器标准
env.Append(CPPFLAGS=['-std=c++17'])

# 添加包含路径
env.Append(CPPPATH=[
    'include',           # 本地头文件
    'third_party/zip',   # 解压库头文件
    '/usr/include'       # 系统头文件
])

# 添加库路径
env.Append(LIBPATH=[
    'lib',              # 本地静态库
    'third_party/lib',  # 第三方库
    '/usr/lib'          # 系统库
])

# 链接库文件
env.Append(LIBS=[
    'zip',              # libzip.a 或 libzip.so
    'z',                # libz.a (zlib)
    'pthread'           # 线程库
])

# 源文件
sources = [
    'src/main.cpp',
    'src/zip_extractor.cpp',
    'src/file_manager.cpp'
]

# 构建目标
program = env.Program(
    target='zip_extractor',  # 输出文件名
    source=sources          # 源文件列表
)

# 默认目标
Default(program)
```
### godot
```rust
scons platform=windows \
      builtin_lzma=no \
      lzma_lib_path="C:/vcpkg/installed/x64-windows/lib" \
      lzma_include_path="C:/vcpkg/installed/x64-windows/include"
```