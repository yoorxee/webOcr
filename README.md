# webOcr
WebOcr，基于Google Tessract4机器学习构建中英文离线Ocr项目。 在其基础上提供了http调用的接口，便于你在其他的项目中调用。 并且提供了Docker，便于部署。

# 特性
### 中文识别
快速高识别率

### 模型训练
通过jTessBoxEditor编辑器，进行模型样本训练，提高识别率

### 并发请求
由于模型本身不支持并发，但通过golang协程的方式，具体并发数取决于机器的配置。

# 环境
✔ Python 3.6+
✔ Ubuntu 16.04
✔ ️Ubuntu 18.04
✔ CentOS 7
✔ Docker
✔ Windows

# 最低配置要求
CPU: 1核
内存: 2G
SWAP: 2G

# 安装部署
##安装
QQ：2192200
EMAIL:webw3cs#gmail.com

##运行
###方法1：docker模式
```
docker run -it -d --restart=always -p 8084:8081 ocr:20201230 /www/ocr -c /www/app.toml &
```
###方法2：宿主机执行模式
```
docker run --rm -v ${PWD}:/data 53349c6654c6 tesseract /data/WechatIMG315.jpeg /data/gysl -l chi_sim --dpi 300
```
###方法3：cli命令模式
```
tesseract /11.jpeg out -l chi_sim --dpi 300
```

## 示例
```
curl -vv -X POST -F file=@test.jpeg "http://81.70.50.12:8084/ocr/upload"
```
```
{
    "errno": 0,
    "errmsg": "",
    "data":"我们可以在Confluence上面进行创建  分享和讨论文件  想法，备忘录，规格，实体模型，图表和项目  通过Confluence平台进行小组工作的协同和知识分享。"
}
```

# 原理
### 历史
Tesseract项目最初由惠普实验室支持，1996年被移植到Windows上，1998年进行了C++化。在2005年Tesseract由惠普公司宣布开源。2006年到现在，都由Google公司开发。
### 特性
目前，Tesseract可以识别超过100种语言。也可以用来训练其它的语言。
源码包提供了一个OCR的引擎——libtesseract以及一个命令行程序——tesseract。
Tesseract支持多种输出格式，如：普通文本、html、pdf等。
### 升级
Tesseract 该软件包包含一个OCR引擎 -  libtesseract和一个命令行程序 -  tesseract。 Tesseract 4增加了一个基于OCR引擎的新神经网络（LSTM），该引擎专注于线路识别，但仍然支持Tesseract 3的传统Tesseract OCR引擎，该引擎通过识别字符模式来工作。通过使用Legacy OCR Engine模式（--oem 0）启用与Tesseract 3的兼容性。它还需要训练有素的数据文件，这些文件支持传统引擎。

