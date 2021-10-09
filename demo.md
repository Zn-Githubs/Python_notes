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
      //标签[contains(@属性名, "开头相同字符串")]
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
