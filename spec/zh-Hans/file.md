# 文件

本文档介绍HyFile中「文件」对象在数据库中的详情。

所有文件对象位于数据库`files`表中，在当前版本(0.1)中，有34个字段，包括17项**基本属性**、16项**私有属性**，以及一个特殊字段`file_itself`，类型为`BLOB`，用于直接在数据库存放文件的情况（但并不推荐此做法）。

## 基本属性

每个文件条目具有17项基本属性，字段信息如下：

| 名称             | 类型   | 长度 | 允许NULL | 注释                 |
| ---------------- | ------ | ---- | -------- | -------------------- |
| UUID             | TEXT   | 36   | 否       |                      |
| name             | TEXT   | 128  | 否       | 文件的原始文件名     |
| source           | TEXT   | 36   | 是       | UUID字符串           |
| path             | TEXT   | 512  | 是       |                      |
| mimetype         | TEXT   | 32   | 是       |                      |
| size             | BIGINT |      | 否       |                      |
| owner            | TEXT   | 36   | 是       | UUID字符串           |
| file_creat_time  | TIME   |      | 否       |                      |
| file_modify_time | TIME   |      | 否       |                      |
| lib_create_time  | TIME   |      | 否       | 在资料库中的创建时间 |
| lib_modify_time  | TIME   |      | 否       | 在资料库中的修改时间 |
| tags             | TEXT   | 512  | 是       | 以半角逗号(`,`)分割  |
| description      | TEXT   | 4096 | 是       |                      |
| version          | TEXT   | 64   | 是       |                      |
| md5              | TEXT   | 32   | 是       |                      |
| sha256           | TEXT   | 64   | 是       |                      |
| sha512           | TEXT   | 128  | 是       |                      |

## 私有属性

私有属性是某些特定文件类型才会有的属性。

| 名称          | 类型   | 长度 | 允许NULL | 注释                     |
| ------------- | ------ | ---- | -------- | ------------------------ |
| thumbnail     | BLOB   |      | 是       | 缩略图                   |
| width         | INT    |      | 是       | 媒体宽度                 |
| height        | INT    |      | 是       | 媒体高度                 |
| duration      | INT    |      | 是       | 音视频时长               |
| latitude      | FLOAT  |      | 是       | 拍摄地点（纬度）         |
| longitude     | FLOAT  |      | 是       | 拍摄地点（经度）         |
| altitude      | FLOAT  |      | 是       | 拍摄地点（高度）         |
| color_space   | TEXT   | 16   | 是       | 媒体色彩空间             |
| camera_info   | TEXT   | 128  | 是       | 相机制造商、型号等       |
| author        | TEXT   | 128  | 是       | 文档作者                 |
| language      | TEXT   | 8    | 是       | 文档语言                 |
| words         | INT    |      | 是       | 文档字数                 |
| pages         | INT    |      | 是       | 文档页数                 |
| album         | TEXT   | 128  | 是       | 音乐专辑/相册名称        |
| bitrate       | INT    |      | 是       | 音视频比特率             |
| original_size | BIGINT |      | 是       | 原始文件大小（压缩文件） |
