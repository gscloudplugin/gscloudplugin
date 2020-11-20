# 光速云插件
- 联系QQ：623105084
- [购买无水印版地址](https://item.taobao.com/item.htm?id=558385485374)
## 特点
- 免费浏览器打印PDF/HTML/图片/Word文档/Excel/PPT/指令打印/自定义绘图。
- 支持超大PDF文件打印，能够快速响应打印。
- 使用静默方式打印。
- 读取串口数据。
- 读取电子秤重量。
- 支持谷歌、火狐、IE7+等浏览器。
- 支持HTTPS协议的站点。
- 跨平台，支持Windows、Linux、Mac、Android系统

## 安装
- [Windows版下载地址](https://gitee.com/gscloudplugin/gscloudplugin/raw/master/setup/光速云插件5.0.5.zip) 当前版本5.0.5
- [Linux版下载地址](https://gitee.com/gscloudplugin/gscloudplugin/raw/master/setup/linux/gscloudplugin_1.0.1.zip) 当前版本1.0.1
- [Mac版下载地址](https://gitee.com/gscloudplugin/gscloudplugin/raw/master/setup/mac/gscloudplugin_v1.0.1.dmg) 当前版本1.0.1
- [Android版下载地址](https://gitee.com/gscloudplugin/gscloudplugin/raw/master/setup/android/光速云插件1.0.1.zip) 当前版本1.0.1，支持蓝牙打印机：佳博、芝柯、斑马，支持Wifi打印机：斑马
- 解压zip文件后，内含安装包和demo文件

## 文档
- 关于尺寸相关单位在文档中未说明的则统一为：毫米
- [打印设计](https://github.com/gscloudplugin/gscloudplugin/blob/master/PrintDesign.md)
- [打印PDF](#1-打印pdf)
- [打印图片](#2-打印图片)
- [打印HTML](#3-打印HTML)
- [打印Word文档](#4-打印Word文档)
- [打印自定义绘图](#5-打印自定义绘图)
- [下载文件](#6-下载文件)
- [异步下载文件](#7-异步下载文件)
- [成功回调事件](#8-成功回调事件)
- [错误回调事件](#9-错误回调事件)
- [获取打印机信息](#10-获取打印机信息)
- [获取打印队列](#11-获取打印队列)
- [读取串口数据](#12-读取串口数据)
- [关闭串口](#13-关闭串口)
- [写入数据到串口](#14-写入数据到串口)
- [写入数据行到串口](#15-写入数据行到串口)
- [写入字节数据到串口](#16-写入字节数据到串口)
- [客户端直接通过http方式调用光速云打印插件](#17-客户端直接通过http方式调用光速云打印插件)
- [Vue项目中调用插件](#18-Vue项目中调用插件)

<a href="#打印PDF"></a>
### 1. 打印PDF
```
GSCloudPlugin.PrintPdf({
			Title:"PDF0001",
			Width: 100,
			Height: 150,
			Url: "https://domain/demo.pdf",
			PrinterName: "",
			OnSuccess:function(result){
				console.log(result);
			},
			OnError:function(result){
				console.log(result);
			}
		     });
```
#### 字段说明
属性 | 说明 | 类型 | 默认值
----|-----|------|------
| Title | 标题| String | 默认GUID格式字符串|
| Width | 纸张宽度。单位毫米 | Int | 0 |
| Height | 纸张高度。单位毫米；值为0时，打印高度自适应，应用于连续纸张 | Int | 0 |
| Url | PDF文件地址 | String | 无 |
| PrinterName | 打印机名称。不传值则使用默认打印机 | String | 无 |
| Pages | 指定打印页码。例：值为"2,5"，指定打印第2、3、4、5页；如果只需打印第2页，设置值为"2" | String | 无 |
| UseFileCache | 适用于大文件。需要先调用[下载文件](#6-下载文件)或[异步下载文件](#7-异步下载文件)，**注意：并且需要设置Title一致** | bool | false  |
| RemoveMargin | 移除空白边距。适用于四周有较大的空白边距的不正规PDF文档；当然其他的类型打印也可以使用该参数 | bool | false |
| Cookies | cookie | Array([Cookie](#Cookie的字段说明)) | 无 |
| HttpHeaders | http头信息 | Array([HttpHeader](#HttpHeader的字段说明)) | 无 |
| Copies | 打印文档份数 | Int | 1 |
| IsAsync | 是否异步；如果为true，则每打印完一页，就会回调一次；如果为false，则等到全部页打印完，才回调一次。支持浏览器：谷歌、火狐、IE10+ | bool | false |
| Duplex | 双面打印 | String | Default（打印机默认的双面打印设置）、Simplex（单面打印）、Vertical（双面垂直打印）、Horizontal（双面水平打印） |
| PaperSource | 纸张来源 | String |  |

<a href="#打印图片"></a>
### 2. 打印图片
```
GSCloudPlugin.PrintImage({
			Title:"PNG0001",
			Width: 100,
			Height: 150,
			Url: "https://domain/demo.png",
			PrinterName: "",
			OnSuccess:function(result){
				console.log(result);
			},
			OnError:function(result){
				console.log(result);
			}
		     });
```
#### 字段说明
属性 | 说明 | 类型 | 默认值
----|-----|------|------
| Title | 标题| String | 默认GUID格式字符串|
| Width | 纸张宽度。单位毫米 | Int | 0 |
| Height | 纸张高度。单位毫米；值为0时，打印高度自适应，应用于连续纸张 | Int | 0  |
| Url | 图片文件地址 | String | 无 |
| PrinterName | 打印机名称。不传值则使用默认打印机 | String | 无 |
| Cookies | cookie | Array([Cookie](#Cookie的字段说明)) | 无  |
| HttpHeaders | http头信息 | Array([HttpHeader](#HttpHeader的字段说明)) | 无  |
| Copies | 打印文档份数 | Int | 1 |
| Duplex | 双面打印 | String | Default（打印机默认的双面打印设置）、Simplex（单面打印）、Vertical（双面垂直打印）、Horizontal（双面水平打印） |
| PaperSource | 纸张来源 | String |  |

<a href="#打印HTML"></a>
### 3. 打印HTML
```
GSCloudPlugin.PrintHtml({
			Title:"HTML0001",
			Width: 210,
			Height: 297,
			Url: "https://domain/demo.html",
			PrinterName: "",
			OnSuccess:function(result){
				console.log(result);
			},
			OnError:function(result){
				console.log(result);
			}
		     });
```
#### 字段说明
属性 | 说明 | 类型 | 默认值
----|-----|------|------
| Title | 标题| String | 默认GUID格式字符串|
| Width | 纸张宽度。单位毫米 | Int | 0 |
| Height | 纸张高度。单位毫米；值为0时，打印高度自适应，应用于连续纸张 | Int | 0  |
| Url | HTML网页地址 | String | 无  |
| PrinterName | 打印机名称。不传值则使用默认打印机 | String | 无 |
| Cookies | cookie | Array([Cookie](#Cookie的字段说明)) | 无  |
| HttpHeaders | http头信息 | Array([HttpHeader](#HttpHeader的字段说明)) | 无  |
| Copies | 打印文档份数 | Int | 1 |
| Duplex | 双面打印 | String | Default（打印机默认的双面打印设置）、Simplex（单面打印）、Vertical（双面垂直打印）、Horizontal（双面水平打印） |
| PaperSource | 纸张来源 | String |  |

<a href="#打印Word文档"></a>
### 4. 打印Word文档
```
GSCloudPlugin.PrintWord({
			Title:"Word0001",
			Width: 210,
			Height: 297,
			Url: "https://domain/demo.docx",
			PrinterName: "",
			OnSuccess:function(result){
				console.log(result);
			},
			OnError:function(result){
				console.log(result);
			}
		     });
```
#### 字段说明
属性 | 说明 | 类型 | 默认值
----|-----|------|------
| Title | 标题| String | 默认GUID格式字符串|
| Width | 纸张宽度。单位毫米 | Int | 0 |
| Height | 纸张高度。单位毫米；值为0时，打印高度自适应，应用于连续纸张 | Int | 0  |
| Url | Word文档地址 | String | 无  |
| PrinterName | 打印机名称。不传值则使用默认打印机 | String | 无 |
| Cookies | cookie | Array([Cookie](#Cookie的字段说明)) | 无  |
| HttpHeaders | http头信息 | Array([HttpHeader](#HttpHeader的字段说明)) | 无  |
| Copies | 打印文档份数 | Int | 1 |

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
			PrinterName: "",
			OnSuccess:function(result){
				console.log(result);
			},
			OnError:function(result){
				console.log(result);
			}
		     });
```
#### 字段说明
属性 | 说明 | 类型 | 默认值
----|-----|------|------
| Title | 标题| String | 默认GUID格式字符串 |
| Width | 纸张宽度。单位毫米 | Int | 0 |
| Height | 纸张高度。单位毫米；值为0时，打印高度自适应，应用于连续纸张 | Int | 0 |
| PrinterName | 打印机名称。不传值则使用默认打印机 | String | 无 |
| Texts | 文本。**该字段也适用于PDF、图片、HTML、Word打印** | Array([Text](#Text的字段说明)) | 无 |
| Lines | 线条。**该字段也适用于PDF、图片、HTML、Word打印** | Array([Line](#Line的字段说明)) | 无 |
| Rectangles | 矩形。**该字段也适用于PDF、图片、HTML、Word打印** | Array([Rectangle](#Rectangle的字段说明)) | 无 |
| Ellipses | 圆形。**该字段也适用于PDF、图片、HTML、Word打印** | Array([Ellipse](#Ellipse的字段说明)) | 无 |
| Barcodes | 条码。**该字段也适用于PDF、图片、HTML、Word打印** | Array([Barcode](#Barcode的字段说明)) | 无 |
| Images | 图片。**该字段也适用于PDF、图片、HTML、Word打印** | Array([Image](#Image的字段说明)) | 无 |
| Htmls | Html。**该字段也适用于PDF、图片、HTML、Word打印** | Array([Html](#Html的字段说明)) | 无 |
| Cookies | cookie | Array([Cookie](#Cookie的字段说明)) | 无  |
| HttpHeaders | http头信息 | Array([HttpHeader](#HttpHeader的字段说明)) | 无  |
| Copies | 打印文档份数 | Int | 1 |
| PrintMethod | 打印方式；值：Print（打印）、Preview（预览）、Design（设计） | String | Print |
| Duplex | 双面打印 | String | Default（打印机默认的双面打印设置）、Simplex（单面打印）、Vertical（双面垂直打印）、Horizontal（双面水平打印） |
| PaperSource | 纸张来源 | String |  |

<a href="#Text的字段说明"></a>
#### Text的字段说明
属性 | 说明 | 类型 | 默认值
----|-----|------|------
| X | 起始坐标X。坐标原点为左上方 | float | 0 |
| Y | 起始坐标Y。坐标原点为左上方 | float | 0 |
| Width | 文本宽度范围 | float | 0 |
| Height | 文本高度范围 | float | 0 |
| Content | 内容| String | 无 |
| FontSize | 文字大小，单位：PT | float | 10 |
| FontFamily | 字体 | String | 系统字体 |
| Color | 颜色。RGBA用","隔开 | String | 0,0,0 |
| LineSpacing | 行距，单位PT | float | 0 |
| Trimming | 文本修整方式。值：None（不进行任何修整）、Character（将文本修整成最接近的字符）、Word（将文本修整成最接近的单词）、EllipsisCharacter（将文本修整成最接近的字符，并在被修整的行的末尾插入一个省略号）、EllipsisWord（将文本修整成最接近的单词，并在被修整的行的末尾插入一个省略号）、EllipsisPath（中心从被修整的行移除并用省略号替换） | String | None |
| Alignment | 文本水平对齐方式。值：Left（左对齐）、Center（居中对齐）、Right（右对齐） | String | Left |
| FontStyle | 字体样式。值：Regular（普通文本）、Bold（加粗文本）、Italic（倾斜文本）、Underline（带下划线的文本）、Strikeout（中间有直线通过的文本） | String | Regular |
| Angle | 角度 | int | 0 |
| SortIndex | 绘制顺序索引 | int | 0 |

<a href="#Line的字段说明"></a>
#### Line的字段说明
属性 | 说明 | 类型 | 默认值
----|-----|------|------
| X | 起始坐标X。坐标原点为左上方 | float | 0 |
| Y | 起始坐标Y。坐标原点为左上方 | float | 0 |
| Width | 文本宽度范围 | float | 0 |
| Height | 文本高度范围 | float | 0 |
| DashStyle | 线条样式。值：Solid（实线）、Dash（由划线段组成的直线）、Dot（由点构成的直线）、DashDot（由重复的划线点图案构成的直线）、DashDotDot（由重复的划线点点图案构成的直线）| String | Solid |
| StrokeWidth | 描边宽度 | float | 0 |
| Color | 颜色。RGBA用","隔开 | String | 0,0,0 |
| SortIndex | 绘制顺序索引 | int | 0 |

<a href="#Rectangle的字段说明"></a>
#### Rectangle的字段说明
属性 | 说明 | 类型 | 默认值
----|-----|------|------
| X | 起始坐标X。坐标原点为左上方 | float | 0 |
| Y | 起始坐标Y。坐标原点为左上方 | float | 0 |
| Width | 文本宽度范围 | float | 0 |
| Height | 文本高度范围 | float | 0 |
| Color | 颜色。RGBA用","隔开 | String | 0,0,0 |
| FillColor | 填充色。RGBA用","隔开 | String | 0,0,0 |
| StrokeWidth | 描边宽度 | float | 0 |
| DashStyle | 线条样式。值：Solid（实线）、Dash（由划线段组成的直线）、Dot（由点构成的直线）、DashDot（由重复的划线点图案构成的直线）、DashDotDot（由重复的划线点点图案构成的直线）| String | Solid |
| Angle | 角度 | int | 0 |
| SortIndex | 绘制顺序索引 | int | 0 |

<a href="#Ellipse的字段说明"></a>
#### Ellipse的字段说明
属性 | 说明 | 类型 | 默认值
----|-----|------|------
| X | 起始坐标X。坐标原点为左上方 | float | 0 |
| Y | 起始坐标Y。坐标原点为左上方 | float | 0 |
| Width | 文本宽度范围 | float | 0 |
| Height | 文本高度范围 | float | 0 |
| Color | 颜色。RGBA用","隔开 | String | 0,0,0 |
| FillColor | 填充色。RGBA用","隔开 | String | 0,0,0 |
| StrokeWidth | 描边宽度 | float | 0 |
| DashStyle | 线条样式。值：Solid（实线）、Dash（由划线段组成的直线）、Dot（由点构成的直线）、DashDot（由重复的划线点图案构成的直线）、DashDotDot（由重复的划线点点图案构成的直线）| String | Solid |
| Angle | 角度 | int | 0 |
| SortIndex | 绘制顺序索引 | int | 0 |

<a href="#Barcode的字段说明"></a>
#### Barcode的字段说明
属性 | 说明 | 类型 | 默认值
----|-----|------|------
| X | 起始坐标X。坐标原点为左上方 | float | 0 |
| Y | 起始坐标Y。坐标原点为左上方 | float | 0 |
| Width | 条码宽度 | float | 0 |
| Height | 条码高度 | float | 0 |
| Format | 条码格式。值：Aztec、Codabar、Code39、Code93、Code128、DataMatrix、EAN8、EAN13、ITF、PDF417、QRCode（二维码）、UPCA、UPCE、MSI、PLESSEY | String | Code128 |
| Text | 文本。 | [BarcodeText](#BarcodeText的字段说明) | 无 |
| TextPosition | 文本位置。值：Top（在条码的上方）、Bottom（在条码的下方） | String | Bottom  |
| Angle | 角度 | int | 0 |
| SortIndex | 绘制顺序索引 | int | 0 |

<a href="#BarcodeText的字段说明"></a>
#### BarcodeText的字段说明
属性 | 说明 | 类型 | 默认值
----|-----|------|------
| Content | 内容。如果不需要显示文本内容，则只设置此字段值，不设置其他字段值 | String | 无 |
| FontSize | 文字大小。单位：PT | float | 0 |
| FontFamily | 字体 | String | 系统字体 |
| Color | 颜色。RGBA用","隔开 | String | 0,0,0 |
| FontStyle | 字体样式。值：Regular（普通文本）、Bold（加粗文本）、Italic（倾斜文本）、Underline（带下划线的文本）、Strikeout（中间有直线通过的文本） | String | Regular |
| HideText | 显示条码文本。只对默认带有文本的条码有效 | bool | true |

<a href="#Image的字段说明"></a>
#### Image的字段说明
属性 | 说明 | 类型 | 默认值
----|-----|------|------
| X | 起始坐标X。坐标原点为左上方 | float | 0 |
| Y | 起始坐标Y。坐标原点为左上方 | float | 0 |
| Width | 条码宽度 | float | 0 |
| Height | 条码高度 | float | 0 |
| Url | 图片地址或Base64编码 | String |    |
| ZoomMode | 缩放模式。值：Ratio（比例缩放）、Distortion（变形缩放）、Origin（原始大小。dpi为96） | String |  Ratio  |
| Angle | 角度 | int | 0 |
| SortIndex | 绘制顺序索引 | int | 0 |

<a href="#Html的字段说明"></a>
#### Html的字段说明
属性 | 说明 | 类型 | 默认值
----|-----|------|------
| X | 起始坐标X。坐标原点为左上方 | float | 0 |
| Y | 起始坐标Y。坐标原点为左上方 | float | 0 |
| Width | 条码宽度 | float | 0 |
| Height | 条码高度 | float | 0 |
| Url | Html地址或Html代码 | String |    |
| Angle | 角度 | int | 0 |
| SortIndex | 绘制顺序索引 | int | 0 |

<a href="#下载文件"></a>
### 6. 下载文件
```
GSCloudPlugin.DownloadFile({
			Title:"File0001",
			Url: url,
			OnSuccess:function(result){
				console.log(result);
			},
			OnError:function(result){
				console.log(result);
			}
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
			Url: url,
			OnSuccess:function(result){
				console.log(result);
			},
			OnError:function(result){
				console.log(result);
			}
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
#### 字段说明
属性 | 说明 | 类型 | 默认值
----|-----|------|------
| Title | 标题。与调用函数时设置的Title值一致 | String | 无 |
| OperationType | 操作类型。值：Print、GetPrinters、DownloadFile、DownloadFileAsync | String | 无 |
| Data | 响应数据。根据调用函数不同而返回不同的数据 | object | 无 |
| Message | 响应消息 | String | 无 |

<a href="#错误回调事件"></a>
### 9. 错误回调事件
#### 字段说明
属性 | 说明 | 类型 | 默认值
----|-----|------|------
| Title | 标题。与调用函数时设置的Title值一致 | String | 无 |
| OperationType | 操作类型。值：Print、GetPrinters、DownloadFile、DownloadFileAsync | String | 无 |
| Message | 响应消息 | String | 无 |
| Code | 错误码 | int | 无 |

<a href="#获取打印机信息"></a>
### 10. 获取打印机信息 
```
GSCloudPlugin.GetPrinterInfo({
		        PrinterName: "",
			OnSuccess:function(result){
				console.log(result);
			},
			OnError:function(result){
				console.log(result);
			}
		     });
```
#### 请求字段说明
属性 | 说明 | 类型 | 默认值
----|-----|------|------
| PrinterName | 打印机名称。不传值则使用默认打印机 | String | 无 |
#### 响应字段说明
属性 | 说明 | 类型
----|-----|------
| Status | 状态。值：0失败、1成功 | String |
| Message | 消息。| String |
| Data | 数据| Object |

#### 响应字段Data说明
属性 | 说明 | 类型
----|-----|------
| CanDuplex | 是否支持双面打印 | bool |
| IsPlotter | 是否是绘图仪 | bool |
| IsDefaultPrinter | 是否默认打印机| bool |
| PrinterName | 打印机名称| String |

<a href="#获取打印队列"></a>
### 11. 获取打印队列 
```
GSCloudPlugin.GetPrintQueue({
			OnSuccess:function(result){
				console.log(result);
			},
			OnError:function(result){
				console.log(result);
			}
		     });
```
#### 响应字段说明
属性 | 说明 | 类型
----|-----|------
| Status | 状态。值：0失败、1成功 | String |
| Message | 消息。| String |
| Data | 数据| Array(Object) |

#### 响应字段Data说明
属性 | 说明 | 类型
----|-----|------
| Name | 任务名；与打印时设置的Title值一致 | String |
| PrinterIndex | 打印机索引号 | Int |
| PrinterName | 打印机名称| String |
| JobStatus | 任务状态；值：None(无指定状态)、Paused(已暂停)、Error(错误)、Deleting(正在删除)、Spooling(正在进行后台打印)、Printing(正在打印)、Offline(脱机状态)、PaperOut(无法提供所需纸张大小)、Printed(已打印)、Deleted(通常情况下，打印完成后，系统会从队列中删除该打印作业)、Blocked(队列中该打印作业之前的打印作业可能出现了错误情况，因此该打印作业已被阻止)、UserIntervention(打印机要求通过用户操作来修复错误情况)、Restarted(打印作业被阻止，但已重新启动)、Completed(打印作业已完成，包括所有打印后处理)、Retained(打印作业打印完后仍保留在打印队列中)| String |
| JobIdentifier | 打印任务标识号| Int |
| TimeJobSubmitted | 提交打印任务时间| String |

<a href="#读取串口数据"></a>
### 12. 读取串口数据 
```
GSCloudPlugin.ReadSerialPortData({
			PortName:"COM2",
			KeepAlive:true,
			OnSuccess:function(result){
				console.log(result);
			},
			OnError:function(result){
				console.log(result);
			}
		});
```
#### 请求字段说明
属性 | 说明 | 类型 | 默认值
----|-----|------|------
| PortName | 端口名 | String | COM1 |
| BaudRate | 波特率 | Int | 9600 |
| Parity | 校验位；值：None(不发生奇偶校验检查)、Odd(奇数)、Even(偶数)、Mark(将奇偶校验位保留为 1)、Space(将奇偶校验位保留为 0) | String | None |
| DataBits | 数据位 | Int | 8 |
| StopBits | 停止位；值：None(不使用停止位)、One(使用一个停止位)、Two(使用两个停止位)、OnePointFive(使用 1.5 个停止位) | String | One |
| KeepAlive | 保持连接；如果值为true，在不需要使用读取串口数据时，建议调用一下关闭串口方法，否则串口会一直被占用，其他程序将无法使用该串口 | bool | true |
#### 响应字段说明
属性 | 说明 | 类型
----|-----|------
| Status | 状态。值：0失败、1成功 | String |
| Message | 消息。| String |
| Data | 数据| String |

<a href="#关闭串口"></a>
### 13. 关闭串口 
```
GSCloudPlugin.CloseSerialPort({
			PortName:"COM2",
			OnSuccess:function(result){
				console.log(result);
			},
			OnError:function(result){
				console.log(result);
			}
		});
```
#### 请求字段说明
属性 | 说明 | 类型 | 默认值
----|-----|------|------
| PortName | 端口名 | String | COM1 |


<a href="#写入数据到串口"></a>
### 14. 写入数据到串口 
```
GSCloudPlugin.WriteSerialPortData({
			PortName:"COM1",
			Text:"123456",
			OnSuccess:function(result){
				console.log(result);
			},
			OnError:function(result){
				console.log(result);
			}
		});
```
#### 请求字段说明
属性 | 说明 | 类型 | 默认值
----|-----|------|------
| Text | 写入的文本数据 | String | 无 |
| PortName | 端口名 | String | COM1 |
| BaudRate | 波特率 | Int | 9600 |
| Parity | 校验位；值：None(不发生奇偶校验检查)、Odd(奇数)、Even(偶数)、Mark(将奇偶校验位保留为 1)、Space(将奇偶校验位保留为 0) | String | None |
| DataBits | 数据位 | Int | 8 |
| StopBits | 停止位；值：None(不使用停止位)、One(使用一个停止位)、Two(使用两个停止位)、OnePointFive(使用 1.5 个停止位) | String | One |


<a href="#写入数据行到串口"></a>
### 15. 写入数据行到串口 
```
GSCloudPlugin.WriteSerialPortData({
			PortName:"COM1",
			Text:"123456",
			OnSuccess:function(result){
				console.log(result);
			},
			OnError:function(result){
				console.log(result);
			}
		});
```
#### 请求字段说明
属性 | 说明 | 类型 | 默认值
----|-----|------|------
| Text | 写入的文本数据 | String | 无 |
| PortName | 端口名 | String | COM1 |
| BaudRate | 波特率 | Int | 9600 |
| Parity | 校验位；值：None(不发生奇偶校验检查)、Odd(奇数)、Even(偶数)、Mark(将奇偶校验位保留为 1)、Space(将奇偶校验位保留为 0) | String | None |
| DataBits | 数据位 | Int | 8 |
| StopBits | 停止位；值：None(不使用停止位)、One(使用一个停止位)、Two(使用两个停止位)、OnePointFive(使用 1.5 个停止位) | String | One |


<a href="#写入字节数据到串口"></a>
### 16. 写入字节数据到串口 
```
GSCloudPlugin.WriteSerialPortData({
			PortName:"COM1",
			Bytes:"10,11,12",
			OnSuccess:function(result){
				console.log(result);
			},
			OnError:function(result){
				console.log(result);
			}
		});
```
#### 请求字段说明
属性 | 说明 | 类型 | 默认值
----|-----|------|------
| Bytes | 写入的字节数据。多个字节使用英文逗号隔开 | String | 无 |
| PortName | 端口名 | String | COM1 |
| BaudRate | 波特率 | Int | 9600 |
| Parity | 校验位；值：None(不发生奇偶校验检查)、Odd(奇数)、Even(偶数)、Mark(将奇偶校验位保留为 1)、Space(将奇偶校验位保留为 0) | String | None |
| DataBits | 数据位 | Int | 8 |
| StopBits | 停止位；值：None(不使用停止位)、One(使用一个停止位)、Two(使用两个停止位)、OnePointFive(使用 1.5 个停止位) | String | One |


<a href="#客户端直接通过http方式调用光速云打印插件"></a>
### 17. 客户端直接通过http方式调用光速云打印插件
URL：http://host:8365/print  其中host为客户端的内网ip地址  
Method：POST  
Content-Type：application/json  

#### 请求字段说明（其他字段参照PDF/图片/HTML/Word的打印字段说明）
属性 | 说明 | 类型 | 默认值
----|-----|------|------
| MediumType | 文档类型。值：Pdf、Image、Html、Word、Draw | String | 无 |
| OperationType | 操作类型。值：Print、GetPrinters、DownloadFile、DownloadFileAsync | String | 无 |
| AppKey | 注册码 | String | 无 |
#### 响应字段说明
属性 | 说明 | 类型
----|-----|------
| Status | 状态。值：0失败、1成功 | String |
| Message | 消息。| String |

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

<a href="#Vue项目中调用插件"></a>
### 18. Vue项目中调用插件
[下载GSCloudPluginFuncs.js压缩包文件](https://gitee.com/gscloudplugin/gscloudplugin/raw/master/GSCloudPluginFuncs.zip)
#### 在项目中引用js文件
```
import {getGSCloudPlugin} from './GSCloudPluginFuncs'
```
#### 获取GSCloudPlugin对象
```
let GSCloudPlugin = getGSCloudPlugin();
```
