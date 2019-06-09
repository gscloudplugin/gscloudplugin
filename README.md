# 光速云插件
## 特点
- 浏览器打印PDF/HTML/图片/自定义绘图。
- 使用静默方式打印。

## 安装
- [下载地址](https://raw.githubusercontent.com/gscloudplugin/gscloudplugin/master/光速云插件3.1.0.zip)
- 解压zip文件后，内含安装包和demo文件

## 文档
- 关于尺寸相关单位统一为：毫米
### 一、打印PDF
```
GSCloudPlugin.PrintPdf({
			Title:"PDF0001",
			Width: 100,
			Height: 150,
			Url: "https://domain/demo.pdf",
			PrinterIndex: -1
		       });
```
### 字段说明
属性 | 说明 | 类型 | 默认值
----|-----|------|------
| Title | 标题| String   | 默认GUID格式字符串|
| Width | 纸张宽度，单位毫米 | Int   | 0 |
| Height | 纸张高度，单位毫米 | Int | 0  |
| Url | PDF文件地址 | String | 无  |
| PrinterIndex | 系统打印机索引号。设置-1使用默认打印机 | Int | -1  |

### 二、打印图片
```
GSCloudPlugin.PrintImage({
			Title:"PNG0001",
			Width: 100,
			Height: 150,
			Url: "https://domain/demo.png",
			PrinterIndex: -1
		       });
```
### 字段说明
属性 | 说明 | 类型 | 默认值
----|-----|------|------
| Title | 标题| String   | 默认GUID格式字符串|
| Width | 纸张宽度，单位毫米 | Int   | 0 |
| Height | 纸张高度，单位毫米 | Int | 0  |
| Url | 图片文件地址 | String | 无  |
| PrinterIndex | 系统打印机索引号。设置-1使用默认打印机 | Int | -1  |

### 三、打印HTML
```
GSCloudPlugin.PrintHtml({
			Title:"HTML0001",
			Width: 100,
			Height: 150,
			Url: url,
			PrinterIndex: printerIndex
		       });
```
### 字段说明
属性 | 说明 | 类型 | 默认值
----|-----|------|------
| Title | 标题| String   | 默认GUID格式字符串|
| Width | 纸张宽度，单位毫米 | Int   | 0 |
| Height | 纸张高度，单位毫米 | Int | 0  |
| Url | HTML网页地址 | String | 无  |
| PrinterIndex | 系统打印机索引号。设置-1使用默认打印机 | Int | -1  |

### 四、打印自定义绘图
```
GSCloudPlugin.PrintDraw({
			Title:"DRAW0001",
			Width: 60,
			Height: 20,
			Texts:[
				{Content:"宇宙飞船",FontSize:2.6,X:1,Y:10,Width:48,Trimming:"EllipsisCharacter",Alignment:"Center"},
				{Content:"Spacecraft",FontSize:2.6,X:1,Y:13,Width:48,Alignment:"Center"},
				{Content:"Mede in China",FontSize:2.6,X:1,Y:16,Width:48,FontStyle:"Bold"}
			],
			Barcodes:[
				{Width:58,Height:9,Format:"CODE_128",X:1,Y:1,Text:{Content:"001AEDWSDFR",FontSize:2.6,Position:"Top"}},
				{Width:9,Height:9,Format:"QR_CODE",X:49,Y:10.5,Text:{Content:"001AEDWSDFR"}}
			],
			PrinterIndex: -1
		});
```
### 字段说明
属性 | 说明 | 类型 | 默认值
----|-----|------|------
| Title | 标题| String   | 默认GUID格式字符串|
| Width | 纸张宽度，单位毫米 | Int   | 0 |
| Height | 纸张高度，单位毫米 | Int | 0  |
| PrinterIndex | 系统打印机索引号。设置-1使用默认打印机 | Int | -1  |
| Texts | 文本 | Array([Text](#Text的字段说明)) | 无  |
| Lines | 线条 | Array(Line) | 无  |
| Barcodes | 条码 | Array(Barcode) | 无  |
### Text的字段说明
<a href="#Text的字段说明"></a>
属性 | 说明 | 类型 | 默认值
----|-----|------|------
| Content | 内容| String   | 无 |
| FontSize | 文字大小 | float   | 0 |
| FontFamilies | 字体。取数组中客户端系统中第一个存在的字体 | Array(String) | 系统字体 |
| Color | 颜色。RGBA用","隔开 | String | 0,0,0 |
| X | 起始坐标X。坐标原点为左上方 | float | 0 |
| Y | 起始坐标Y。坐标原点为左上方 | float | 0 |
| Width | 文本宽度范围。如果值小于等于0，则为打印纸张宽度 | float | 0 |
| Height | 文本高度范围。如果值小于等于0，则为一行文本的高度；如果需要多行文本，则将值设置多行的高度，注意：根据字体的不同，一行的高度要大于设置的FontSize的值，参考值：在FontSize的值基础上增加，请根据实际情况进行调整 | float | 0 |
| Trimming | 文本修整方式。值：None（不进行任何修整）、Character（将文本修整成最接近的字符）、Word（将文本修整成最接近的单词）、EllipsisCharacter（将文本修整成最接近的字符，并在被修整的行的末尾插入一个省略号）、EllipsisWord（将文本修整成最接近的单词，并在被修整的行的末尾插入一个省略号）、EllipsisPath（中心从被修整的行移除并用省略号替换） | String | None |
| Alignment | 文本水平对齐方式。值：Left（左对齐）、Center（居中对齐）、Right（右对齐） | String | Left |
| VerticalAlignment | 文本垂直对齐方式。值：Top（顶部对齐）、Center（居中对齐）、Bottom（底部对齐） | String | Top |
| FontStyle | 字体样式。值：Regular（普通文本）、Bold（加粗文本）、Italic（倾斜文本）、Underline（带下划线的文本）、Strikeout（中间有直线通过的文本） | String | Regular |
### Line的字段说明
属性 | 说明 | 类型 | 默认值
----|-----|------|------
| DashStyle | 线条样式。值：Solid（实线）、Dash（由划线段组成的直线）、Dot（由点构成的直线）、DashDot（由重复的划线点图案构成的直线）、DashDotDot（由重复的划线点点图案构成的直线）| String   | Solid|
| StrokeWidth | 描边宽度 | float   | 0 |
| Color | 颜色。RGBA用","隔开 | String | 0,0,0  |
| Points | 点。由很多个点组成线条，如："0,0,10,0,10,10,0,10,0,0" 组成一个正方形，每两个数值组成一个坐标点xy，坐标原点为左上方 | Array(float) | 无  |
