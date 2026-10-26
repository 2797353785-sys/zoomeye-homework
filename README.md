# zoomeye-homework

# 网络资产搜索与子域名收集实践

## 一、实验目的

了解网络资产搜索引擎的用途，学习 ZoomEye 的基本搜索语法，
并通过公开收录的信息收集、整理子域名。

本次实验以 mozilla.org 为示例，仅查询平台已有的公开记录。

## 二、与 ZoomEye 功能类似的搜索引擎

| 平台 | 主要用途 |
|---|---|
| FOFA | 查询互联网资产，可根据域名、IP、端口、网站标题等条件检索 |
| Shodan | 查询互联网连接设备及其服务信息 |
| Censys | 查询互联网主机、网站和证书相关信息 |
| Hunter（鹰图） | 根据域名、IP、应用指纹等信息检索网络资产 |

这些平台的检索语法和数据覆盖范围有所不同，使用前需要查看各自的语法说明。

## 三、ZoomEye 搜索实践

### 1. 打开平台

打开 ZoomEye，登录账号，查看搜索语法说明。

<img width="2559" height="1398" alt="1" src="https://github.com/user-attachments/assets/c917668c-6811-433e-a543-d099458048de" />


### 2. 输入查询条件

在搜索框输入：

    domain="mozilla.org"

根据平台语法说明，domain 条件用于查询域名及子域名相关的资产。

### 3. 查看查询结果

本次查询页面显示约487条结果，其中最近一年数据448条。
结果数量会随平台数据更新而变化。

<img width="2514" height="1236" alt="2" src="https://github.com/user-attachments/assets/880760d6-f956-45b5-85ad-42052a4dd34b" />


搜索结果可以展示域名、端口、协议、应用指纹及 HTTP 响应头等信息。

例如，addons.mozilla.org 的80端口记录显示 HTTP 301 重定向，
Location 字段指向 https://addons.mozilla.org/。

这些信息是平台收录时的记录，不代表目标当前的实时状态。

## 四、子域名收集与整理

### 1. 收集方法

本次使用 ZoomEye 已收录的域名数据进行被动收集：

1. 使用 domain="mozilla.org" 进行查询。
2. 浏览结果，提取以 .mozilla.org 结尾的域名。
3. 去除端口号、协议和路径。
4. 对重复域名去重，整理成表格。

例如，addons.mozilla.org:80 和 addons.mozilla.org:443
属于同一个子域名的不同服务记录，只统计一次。

### 2. 整理结果

从本次查看的结果中，整理出以下6个不同子域名：

| 序号 | 子域名 |
|---|---|
| 1 | addons.mozilla.org |
| 2 | monitor.mozilla.org |
| 3 | vpn.mozilla.org |
| 4 | developer.mozilla.org |
| 5 | www.mozilla.org |
| 6 | support.mozilla.org |

<img width="2040" height="1050" alt="03-子域名收集-1" src="https://github.com/user-attachments/assets/acfe825a-5f07-4e14-b700-2997111a63c2" />
<img width="2025" height="1062" alt="03-子域名收集-2" src="https://github.com/user-attachments/assets/c9792ca8-65ae-405a-a6ea-8361a52e5c78" />
<img width="2031" height="1026" alt="03-子域名收集-3" src="https://github.com/user-attachments/assets/97d57a12-7603-462a-8c50-2094841eb3c5" />
<img width="1962" height="1056" alt="03-子域名收集-4" src="https://github.com/user-attachments/assets/71f71e7b-8b38-4cf5-ba0c-fa0b654e3cd8" />
<img width="2028" height="1037" alt="03-子域名收集-5" src="https://github.com/user-attachments/assets/0eb71fd3-9908-48c4-8eb0-fbff7975ae50" />



以上是本次人工整理的部分结果，并非 mozilla.org 的完整子域名清单。
平台显示的487条资产记录，也不等于487个不同子域名。

## 五、实验总结

通过本次实验，我了解了 ZoomEye 及同类网络资产搜索引擎的用途，
掌握了 domain 查询条件的基本用法。

在整理结果时，我认识到同一个域名可以对应多个端口和服务记录，
因此统计子域名时需要先提取域名，再进行去重。

网络资产搜索引擎能够辅助信息收集，但其数据具有收录范围和更新时间的限制，
不能将查询结果直接视为完整、实时的资产清单。
