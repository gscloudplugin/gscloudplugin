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
| Texts | 文本 | Array(Text) | 无  |
| Lines | 线条 | Array(Line) | 无  |
| Barcodes | 条码 | Array(Barcode) | 无  |
### Line的字段说明
属性 | 说明 | 类型 | 默认值
----|-----|------|------
| DashStyle | 线条样式，值：Solid（实线）、Dash（由划线段组成的直线）、Dot（由点构成的直线）、DashDot（由重复的划线点图案构成的直线）、DashDotDot（由重复的划线点点图案构成的直线）| String   | Solid|
| StrokeWidth | 描边宽度 | float   | 0 |
| Color | 颜色，RGBA格式 | String | 0,0,0  |
| Points | 点，由很多个点组成线条，如："0,0,10,0,10,10,0,10,0,0" 组成一个正方形，每两个数组成一个坐标点xy，坐标原点为坐上方 | Array(float) | 无  |
