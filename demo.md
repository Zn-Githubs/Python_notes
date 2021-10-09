# XPath
> 为了使用xpath，需要安装lxml
> XPath返回的是一个列表

`pip install lxml`
## 语法
1. 获取文本:
```python
//标签1[@属性1="属性1"]/标签2[@属性2="属性2"]/.../text()
```
2. 获取属性值：
```python
//标签1[@属性1="属性值1”]/标签2[@属性2="属性2"]/.../@属性n
```
3. XPath特殊情况
   1. 以相同字符串开头
      ```python
      //标签[starts-with(@属性名, "开头相同字符串")]
      ```
   2. 属性值包含相同字符串
      ```python
      //标签[contains(@属性名, "相同字符串")]
      ```
   3. 对Xpath返回的对象执行XPath
      例：
      ```python
      useful = html.xpath('//div[@class="useful"]')# 这里返回一个列表
      info_list = useful[0].xpath('ul/li/text()')
      ```
   4. 不同标签下的文字
      ```python
      useful = html.xpath('//div[@id="test1"]')[0]
      info = useful.xpath('string(.)')
      ```
# Beautiful Soup4
## 安装
`pip install beautifulsoup4`
## 导入
`from bs4 import BeautifulSoup`
## 语法
步骤：
   1. 处理源代码生成的BeautifulSoup对象
   2. 使用find_all()或者find()来查找内容
      1. 解析源代码
         ```python
         soup = BeautifulSoup(网页源代码, '解析器')# 解析器可以使用lxml
         ```
      2. 查找内容
         ```python
         useful = soup.find(class_='useful')
         all_content = useful.find_all('li')
         for li in all_content：
         print(li.string)
         ```
### find()与find_all区别
- find_all()返回的是BeautifulSoup Tag对象组成的列表，如果没有找到符合要求的标签则返回空列表
- find()返回的是一个BeautifulSoup Tag对象，如果有多个符合条件的标签，则返回第1个，找不到则返回None
