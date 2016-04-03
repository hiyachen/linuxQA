在线编辑https://pandao.github.io/editor.md/
http://www.ituring.com.cn/article/10044
1:安装
root@linx:~# apt-get install retext discount python-markdown python-pisa
需要下载 27.2 MB 的软件包。
解压缩后会消耗掉 112 MB 的额外空间。

2:将markdown文件转换成html文件
# 用discount提供的markdown工具
markdown -o Release-Notes.html Release-Notes.md
# 用python-markdown提供的markdown_py工具
markdown_py -o html4 Release-Notest.md > Release-Notes.html


3:将html转换成PDF
# 用python-pisa提供的xhtml2pdf
xhtml2pdf --html Release-Notes.html Release-Notes.pdf

所以，你可以在文档目录下放置这样一个Makefile来自动这个过程：

# Makefile

MD = markdown
MDFLAGS = -T
H2P = xhtml2pdf
H2PFLAGS = --html
SOURCES := $(wildcard *.md)
OBJECTS := $(patsubst %.md, %.html, $(wildcard *.md))
OBJECTS_PDF := $(patsubst %.md, %.pdf, $(wildcard *.md))

all: build

build: html pdf

pdf: $(OBJECTS_PDF)

html: $(OBJECTS)

$(OBJECTS_PDF): %.pdf: %.html
    $(H2P) $(H2PFLAGS) $< > $@

$(OBJECTS): %.html: %.md
    $(MD) $(MDFLAGS) -o $@ $<
clean:
    rm -f $(OBJECTS)这样你就可以通过简单的一个命令生成当前目录下所有md文件的pdf或html输出了：

# html 输出
make html

# pdf输出
make pdf这里有个问题是如果markdown的内容是中文，那么转换出来的html在浏览器中打开就无法自动识别编码，pdf更惨，直接是一堆乱码。这时我们可以借助markdown对html标记的支持来在markdown文件中加入编码信息。例如我们要将markdown转换为html4文件，可以在文件的开头加上meta标记，指明编码格式：

sed -i '1i\<meta http-equiv="content-type" content="text/html; charset=UTF-8">' *.md这样就可以了。另外，最近使用图灵社区的编辑系统时，markdown会时不时将下划线（_）当作斜体的标记，结果函数名就成了这样的：

# 实际上是ssl_use_cabundle
sslusecabundle我建议斜体字标记采用单个星号（*），加粗字体采用两个星号（**），这样使用起来就方便多了。当然，这个问题本身在于markdown说用星号或下划线都可以。但实际上，两个都支持反倒会造成一些问题。比如有的地方用下划线（__粗体__ -> 粗体），有的地方用星号（**粗体** -> 粗体），看起来反倒混乱不堪（选星号*的另一个理由是下划线在内容中出现的概率比星号高很多）。


