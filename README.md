# shenqidaohang
神奇导航
234555.xyz
2020马上过年了，所以只整理了这一部分
2020/1/23
【注意：上传后记得开启伪静态 伪静态规则如果是宝塔直接选择tp5的】
其他的请根据自己的环境决定：

--------
安装地址：http://域名/index.php/install/install/index
后台地址：http://域名/index.php/admin/admin/index.html
统计：http://域名/index.php/index/api/gettongji/

如果安装失败可以手动安装 导入数据库
数据库在shenqidh.zip\application\install\controller 里面
之后修改config/database的数据库连接

收藏和点赞都在js里面
--------
万能标签
table      表名 数据库表名
where      查询条件（默认就不显示未审核数据）
order      排序
id         解析数组名
key        解析key名
limit      分页条数 无论是否分页的条数
page       是否分页false/true
cid        上级ID 支持变量
hcsj       缓存时间
{shenqi:list table="article"  id="vo" key="k" where="" order='addtime desc' cid='$cid' limit='15' page='true'}
根据tp5的方法来调用标签就行
比如要调用文章的标题 {$vo.title}
{/shenqi:list}
--------

--------
来源统计 开启    关闭 *如果不需要统计可关闭
非友联是否统计 统计    不统计 *会统计百度等搜索引擎来源 如果需要减少数据库占用 建议不统计
点出统计 统计    不统计 *会统计百度等搜索引擎来源 如果需要减少数据库占用 建议不统计
来源审核 开启    关闭 *开启后 他站提交收录后从他站访问你站链接 自动审核 否则手动审核
--------
===文章内容页独有标签==
--------
文章相关信息
aid,title,keywords,text,content,hit,zan,addtime,tname,top,status,username,cid,link
{$article.xxx}
--------
相关文章调用article
{volist name="likear" id="vo"}       
{$vo.xxx}      
aid文章id
title文章标题
cid文章分类id
name分类名
text内容
addtime添加时间
hit点击次数
 {/volist}
--------
标签
{volist name="keywords" id="vo"}     
{$vo}显示标签
 {/volist}
--------
====文章分类页cata===
--------
当前分类页相关信息
cid
name
cname
keywords
catakeywords
description
sort
addtime
{$catainfo.xxx}
--------
全部分类
cid,name,cname,keywords,description,sort,addtime
{volist name="cata" id="vo"}
<a {if ($cid eq $vo.cid) }class="active" {/if} href="{:url('cata/index',array('cid'=>$vo['cid']))}" >{$vo.name}</a>
{/volist}
--------
{$cid}当前分类id

====链接分类type=====
当前页面信息
type_id
type_name
type_keywords
type_description
type_status
type_addtime
type_sort
调用{$typeinfo.type_id}
--------
输出全部链接分类
type_id,type_name,type_keywords,type_description,type_status,type_addtime,type_sort,type_enname
{volist name="type" id="vo" }
<a {if ($typeid eq $vo.type_id) }class="active" {/if} href="{:url('type/index',array('tid'=>$vo['type_id']))}" >{$vo.type_name}</a>
 {/volist}
--------

===链接详情页link===
当前页面链接信息
link_id,link_title,link_keywords,link_text,link_url,link_img,link_status,link_hit,link_addtime,link_sort,type_id,link_top,link_intime
{$links.xxxx}

--------
标签
{volist name="keywords" id="vo"}     
{$vo}显示标签
 {/volist}
--------
