# LibcSearcher
此项目整理自项目 [lieanu/LibcSearcher](https://github.com/lieanu/LibcSearcher)，仅更新部分代码。

## 安装

```shell
#install module
git clone --recursive https://github.com/Ma5ker/LibcSearcher.git
cd LibcSearcher
python setup.py develop
#download libc file
cd libc-database
./get
```

## 示例

```python
from LibcSearcher import *

#第二个参数，为已泄露的实际地址,或最后12位(比如：d90)，int类型
obj = LibcSearcher("fgets", 0X7ff39014bd90)

obj.dump("system")        #system 偏移
obj.dump("str_bin_sh")    #/bin/sh 偏移
obj.dump("__libc_start_main_ret")    
```

遇到返回多个libc版本库的情况，可以通过`add_condition(leaked_func, leaked_address)`来添加限制条件，也可以手工选择其中一个libc版本。
