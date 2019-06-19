# 光速云插件
## 特点
- 浏览器打印PDF/HTML/图片/Word文档/自定义绘图。
- 使用静默方式打印。

## 安装
- [下载地址](https://media.githubusercontent.com/media/gscloudplugin/gscloudplugin/master/setup/光速云插件3.1.2.zip)
- 解压zip文件后，内含安装包和demo文件

## 文档
- 关于尺寸相关单位统一为：毫米
- [打印PDF](#1-打印pdf)
- [打印图片](#2-打印图片)
- [打印HTML](#3-打印HTML)
- [打印Word文档](#4-打印Word文档)
- [打印自定义绘图](#5-打印自定义绘图)
- [下载文件](#6-下载文件)
- [异步下载文件](#7-异步下载文件)
- [成功回调事件](#8-成功回调事件)
- [错误回调事件](#9-错误回调事件)

<a href="#打印PDF"></a>
### 1. 打印PDF
```
GSCloudPlugin.PrintPdf({
			Title:"PDF0001",
			Width: 100,
			Height: 150,
			Url: "https://domain/demo.pdf",
			PrinterIndex: -1
		       });
```
#### 字段说明
属性 | 说明 | 类型 | 默认值
----|-----|------|------
| Title | 标题| String | 默认GUID格式字符串|
| Width | 纸张宽度，单位毫米 | Int | 0 |
| Height | 纸张高度，单位毫米 | Int | 0 |
| Url | PDF文件地址 | String | 无 |
| PrinterIndex | 系统打印机索引号。设置-1使用默认打印机 | Int | -1 |
| Pages | 指定打印页码。例：值为"2,5"，指定打印第2、3、4、5页；如果只需打印第2页，设置值为"2" | String | 无 |
| UseFileCache | 适用于大文件。需要先调用[下载文件](#5-下载文件)或[异步下载文件](#6-异步下载文件)，**注意：并且需要设置Title一致** | bool | false  |
| RemoveMargin | 移除空白边距。适用于四周有较大的空白边距的不正规PDF文档；当然其他的类型打印也可以使用该参数 | bool | false |
| Cookies | cookie | Array([Cookie](#Cookie的字段说明)) | 无 |
| HttpHeaders | http头信息 | Array([HttpHeader](#HttpHeader的字段说明)) | 无 |

<a href="#打印图片"></a>
### 2. 打印图片
```
GSCloudPlugin.PrintImage({
			Title:"PNG0001",
			Width: 100,
			Height: 150,
			Url: "https://domain/demo.png",
			PrinterIndex: -1
		       });
```
#### 字段说明
属性 | 说明 | 类型 | 默认值
----|-----|------|------
| Title | 标题| String | 默认GUID格式字符串|
| Width | 纸张宽度，单位毫米 | Int | 0 |
| Height | 纸张高度，单位毫米 | Int | 0  |
| Url | 图片文件地址 | String | 无 |
| PrinterIndex | 系统打印机索引号。设置-1使用默认打印机 | Int | -1  |
| Cookies | cookie | Array([Cookie](#Cookie的字段说明)) | 无  |
| HttpHeaders | http头信息 | Array([HttpHeader](#HttpHeader的字段说明)) | 无  |

<a href="#打印HTML"></a>
### 3. 打印HTML
```
GSCloudPlugin.PrintHtml({
			Title:"HTML0001",
			Width: 210,
			Height: 297,
			Url: "https://domain/demo.html",
			PrinterIndex: -1
		       });
```
#### 字段说明
属性 | 说明 | 类型 | 默认值
----|-----|------|------
| Title | 标题| String | 默认GUID格式字符串|
| Width | 纸张宽度，单位毫米 | Int | 0 |
| Height | 纸张高度，单位毫米 | Int | 0  |
| Url | HTML网页地址 | String | 无  |
| PrinterIndex | 系统打印机索引号。设置-1使用默认打印机 | Int | -1  |
| Cookies | cookie | Array([Cookie](#Cookie的字段说明)) | 无  |
| HttpHeaders | http头信息 | Array([HttpHeader](#HttpHeader的字段说明)) | 无  |


<a href="#打印Word文档"></a>
### 4. 打印Word文档
```
GSCloudPlugin.PrintWord({
			Title:"Word0001",
			Width: 210,
			Height: 297,
			Url: "https://domain/demo.docx",
			PrinterIndex: -1
		       });
```
#### 字段说明
属性 | 说明 | 类型 | 默认值
----|-----|------|------
| Title | 标题| String | 默认GUID格式字符串|
| Width | 纸张宽度，单位毫米 | Int | 0 |
| Height | 纸张高度，单位毫米 | Int | 0  |
| Url | Word文档地址 | String | 无  |
| PrinterIndex | 系统打印机索引号。设置-1使用默认打印机 | Int | -1  |
| Cookies | cookie | Array([Cookie](#Cookie的字段说明)) | 无  |
| HttpHeaders | http头信息 | Array([HttpHeader](#HttpHeader的字段说明)) | 无  |

<a href="#打印自定义绘图"></a>
### 5. 打印自定义绘图
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
#### 字段说明
属性 | 说明 | 类型 | 默认值
----|-----|------|------
| Title | 标题| String | 默认GUID格式字符串 |
| Width | 纸张宽度，单位毫米 | Int | 0 |
| Height | 纸张高度，单位毫米 | Int | 0 |
| PrinterIndex | 系统打印机索引号。设置-1使用默认打印机 | Int | -1 |
| Texts | 文本。**该字段也适用于PDF、图片、HTML、Word打印** | Array([Text](#Text的字段说明)) | 无 |
| Lines | 线条。**该字段也适用于PDF、图片、HTML、Word打印** | Array([Line](#Line的字段说明)) | 无 |
| Barcodes | 条码。**该字段也适用于PDF、图片、HTML、Word打印** | Array([Barcode](#Barcode的字段说明)) | 无 |
| Cookies | cookie | Array([Cookie](#Cookie的字段说明)) | 无  |
| HttpHeaders | http头信息 | Array([HttpHeader](#HttpHeader的字段说明)) | 无  |

<a href="#Text的字段说明"></a>
#### Text的字段说明
属性 | 说明 | 类型 | 默认值
----|-----|------|------
| Content | 内容| String | 无 |
| FontSize | 文字大小 | float | 0 |
| FontFamilies | 字体。取数组中在客户端系统中第一个存在的字体 | Array(String) | 系统字体 |
| Color | 颜色。RGBA用","隔开 | String | 0,0,0 |
| X | 起始坐标X。坐标原点为左上方 | float | 0 |
| Y | 起始坐标Y。坐标原点为左上方 | float | 0 |
| Width | 文本宽度范围。如果值小于等于0，则为打印纸张宽度 | float | 0 |
| Height | 文本高度范围。如果值小于等于0，则为一行文本的高度；如果需要多行文本，则将值设置多行的高度，注意：根据字体的不同，一行的高度要大于设置的FontSize的值，参考值：在FontSize的值基础上增加20%，请根据实际情况进行调整 | float | 0 |
| Trimming | 文本修整方式。值：None（不进行任何修整）、Character（将文本修整成最接近的字符）、Word（将文本修整成最接近的单词）、EllipsisCharacter（将文本修整成最接近的字符，并在被修整的行的末尾插入一个省略号）、EllipsisWord（将文本修整成最接近的单词，并在被修整的行的末尾插入一个省略号）、EllipsisPath（中心从被修整的行移除并用省略号替换） | String | None |
| Alignment | 文本水平对齐方式。值：Left（左对齐）、Center（居中对齐）、Right（右对齐） | String | Left |
| VerticalAlignment | 文本垂直对齐方式。值：Top（顶部对齐）、Center（居中对齐）、Bottom（底部对齐） | String | Top |
| FontStyle | 字体样式。值：Regular（普通文本）、Bold（加粗文本）、Italic（倾斜文本）、Underline（带下划线的文本）、Strikeout（中间有直线通过的文本） | String | Regular |

<a href="#Line的字段说明"></a>
#### Line的字段说明
属性 | 说明 | 类型 | 默认值
----|-----|------|------
| DashStyle | 线条样式。值：Solid（实线）、Dash（由划线段组成的直线）、Dot（由点构成的直线）、DashDot（由重复的划线点图案构成的直线）、DashDotDot（由重复的划线点点图案构成的直线）| String | Solid |
| StrokeWidth | 描边宽度 | float | 0 |
| Color | 颜色。RGBA用","隔开 | String | 0,0,0 |
| Points | 点。由很多个点组成线条，如："0,0,10,0,10,10,0,10,0,0" 组成一个正方形，每两个数值组成一个坐标点xy，坐标原点为左上方 | Array(float) | 无 |

<a href="#Barcode的字段说明"></a>
#### Barcode的字段说明
属性 | 说明 | 类型 | 默认值
----|-----|------|------
| Width | 条码宽度 | float | 0 |
| Height | 条码高度 | float | 0 |
| Format | 条码格式。值：AZTEC、CODABAR、CODE_39、CODE_93、CODE_128、DATA_MATRIX、EAN_8、EAN_13、ITF、MAXICODE、PDF_417、QR_CODE（二维码）、RSS_14、RSS_EXPANDED、UPC_A、UPC_E、All_1D、UPC_EAN_EXTENSION、MSI、PLESSEY、IMB | String | CODE_128 |
| X | 起始坐标X。坐标原点为左上方 | float | 0 |
| Y | 起始坐标Y。坐标原点为左上方 | float | 0 |
| Text | 文本。 | [BarcodeText](#BarcodeText的字段说明) | 无 |
| TextPosition | 文本位置。值：Top（在条码的上方）、Bottom（在条码的下方） | String | Bottom  |

<a href="#BarcodeText的字段说明"></a>
#### BarcodeText的字段说明
属性 | 说明 | 类型 | 默认值
----|-----|------|------
| Content | 内容。如果不需要显示文本内容，则只设置此字段值，不设置其他字段值 | String | 无 |
| FontSize | 文字大小 | float | 0 |
| FontFamilies | 字体。取数组中在客户端系统中第一个存在的字体 | Array(String) | 系统字体 |
| Color | 颜色。RGBA用","隔开 | String | 0,0,0 |

<a href="#下载文件"></a>
### 6. 下载文件
```
GSCloudPlugin.DownloadFile({
			Title:"File0001",
			Url: url
		});
```
#### 字段说明
属性 | 说明 | 类型 | 默认值
----|-----|------|------
| Title | 标题。将会使用此值做为文件名保存 | String | 无 |
| Url | 文件地址 | String | 无 |
| Cookies | cookie | Array([Cookie](#Cookie的字段说明)) | 无  |
| HttpHeaders | http头信息 | Array([HttpHeader](#HttpHeader的字段说明)) | 无  |

<a href="#异步下载文件"></a>
### 7. 异步下载文件
```
GSCloudPlugin.DownloadFileAsync({
			Title:"File0002",
			Url: url
		});
```
#### 字段说明
属性 | 说明 | 类型 | 默认值
----|-----|------|------
| Title | 标题。将会使用此值做为文件名保存 | String | 无 |
| Url | 文件地址 | String | 无 |
| Cookies | cookie | Array([Cookie](#Cookie的字段说明)) | 无  |
| HttpHeaders | http头信息 | Array([HttpHeader](#HttpHeader的字段说明)) | 无  |

<a href="#成功回调事件"></a>
### 8. 成功回调事件
```
GSCloudPlugin.OnSuccess = function(result){
			console.log(result);
		}
```
#### 字段说明
属性 | 说明 | 类型 | 默认值
----|-----|------|------
| Title | 标题。与调用函数时设置的Title值一致 | String | 无 |
| OperationType | 操作类型。值：Print、GetPrinters、DownloadFile、DownloadFileAsync | String | 无 |
| Data | 响应数据。根据调用函数不同而返回不同的数据 | object | 无 |
| Message | 响应消息 | String | 无 |

<a href="#错误回调事件"></a>
### 9. 错误回调事件
```
GSCloudPlugin.OnError = function(message,code,title,operationType){
			console.log(JSON.stringify({Message:message,Code:code,Title:title,OperationType:operationType}));
		}
```
#### 字段说明
属性 | 说明 | 类型 | 默认值
----|-----|------|------
| title | 标题。与调用函数时设置的Title值一致 | String | 无 |
| operationType | 操作类型。值：Print、GetPrinters、DownloadFile、DownloadFileAsync | String | 无 |
| message | 响应消息 | String | 无 |
| code | 错误码 | String | 无 |

### 其他

<a href="#Cookie的字段说明"></a>
#### Cookie的字段说明
属性 | 说明 | 类型 | 默认值
----|-----|------|------
| Domain | 域名。必填，否则无效 | String | 无 |
| Key | 键。必填，否则无效 | String | 无 |
| Value | 值。必填，否则无效 | String | 无 |

<a href="#HttpHeader的字段说明"></a>
#### HttpHeader的字段说明
属性 | 说明 | 类型 | 默认值
----|-----|------|------
| Key | 键。必填，否则无效；值：CacheControl、Authorization、Cookie、Referer | String | 无 |
| Value | 值。必填，否则无效 | String | 无 |
