---
"title": "首页",
"author": "liuwei",
"date": "2018-02-27"

---

## Wikitten 程序修改备忘

> 一直想要一个简单的 markdown 格式的笔记程序，而 [Wikitten](https://github.com/victorstanciu/Wikitten) 正是我想要的，在此感谢作者 [Victor Stanciu](https://github.com/victorstanciu)，由于 Wikitten 没有提供登陆认证机制，任何人在线上都可以修改文件，故稍做修改，在提交修改时增加简单的密码验证功能。

修改如下:

* 在`views/render.php`文件中找到`<input type="submit" class="btn btn-warning btn-sm" id="submit-edits" value="Save Changes">`这行代码，在前面加上一个密码框，代码如下：

```
<div class="form-actions">
   <input type="password" name="pwd"/>
   <input type="submit" class="btn btn-warning btn-sm" id="submit-edits" value="Save Changes">
</div>
``` 

* 在`wiki.php`文件中找到`editAction()`方法，在方法体的最上方加上如下代码：

```
$pwd = $_POST['pwd'];
if ($pwd != "想要设置的密码"){
   echo "NO NO NO, What are you 弄啥咯!!!";
   exit();
}
```
这样，一个简单的验证就做好了。 