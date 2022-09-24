# pip

## pip install

### 不同文件格式

- pip install .whl:
  - 在官网pypi.org下载.whl文件
  - 在该.whl文件夹下pip install .whl
- pip install .tar.gz:
  - 在官网pypi.org下载.tar.gz文件
  - tar -zxvf .tar.gz
  - cd 文件夹
  - python setup.py build
  - python setup.py install

### 指定国内源

```bash
pip install -r requirements.txt -i 源链接
中科大:https://pypi.mirrors.ustc.edu.cn/simple/
清华: https://pypi.tuna.tsinghua.edu.cn/simple
阿里云:http://mirrors.aliyun.com/pypi/simple/
豆瓣:http://pypi.douban.com/simple/
```
