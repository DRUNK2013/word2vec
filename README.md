Google code SVN库代码转换过来<br>
修改部分：<br>
把word2vec.c中，词和数据保存到文件中部分，进行了格式化数据。格式：word|vector，vector是以","分割的一个字符串。<br>
例如：<br> 
什么|-0.344641,0.253179,-0.213941,-0.267701,0.845357,-0.448832,-0.386425,0.025924,0.035819,0.442021,0.398240,0.625807

<br>
修改问题2：关于中英文字符编码问题<br>
word2vec.c,词的长度默认是100，但汉字和英文字符占位不同。<br>
若文件是UTF-8格式，且词长度*4大于设定的词给定的长度，则极有可能会出现位错乱，导致乱码（UTF-8汉字在2-4位不等）。<br>
因此需要预处理词在25字节之内，或者加大MAX_STRING值<br>
#define MAX_STRING 1000 
