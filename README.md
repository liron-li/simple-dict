# simple-dict

#### 声明
本扩展包完全基于[nowgoo/dict](https://github.com/nowgoo/dict "nowgoo/dict") ，由于原作者一直没有发布composer版本，所有才有了此包

#### 安装
```
composer require liron/simple-dict
```

#### 使用说明
- 准备文本文件`words.txt`，每行一个词，`词语`和`值`之间用`制表符（\t）`分割。例如：

```
苹果\t1
香蕉\t2
西瓜\t3
```
*注意：* 一般来说在文本编辑器中制表符是显示空白的

- 生成词典
```
\SimpleDict\SimpleDict::make("./words.txt", "./dict");
```

- 搜索
```
$dict = new SimpleDict("./dict");
$result = $dict->search("我喜欢吃苹果，不喜欢吃香蕉！");

/* $result 的格式：
[
  '苹果' => ['value' => '1', 'count' => '1'],
  '香蕉' => ['value' => '2', 'count' => '1'],
  ...
]
```
- 替换
```
// 简单替换
$replaced = $dict->replace("some text here...", "**");
// 高级替换
$replaced = $dict->replace("some text here...", function($word, $value) {
  return "[$word -> $value]";
});
```