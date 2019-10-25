git clone https://github.com/jim422/GitDemo.git (克隆远程厂库)

### git add .

git add <file> (把工作区的代码提交到暂存区)

### git reset HEAD <file> (取消暂存的文件)

### git commit -m 'message' (把暂存区的代码提交到本地库)

### git reset --hard <commit_id> (重置当前的 HEAD 到一个指定的状态。直接删除该状态后续的所有提交（就像没提交过一样），日志上表现为丢弃对应 commit id 后的所有日志, 不建议使用)

### git push origin <分支名> (将本地库的代码推送到远程服务器上)

### git branch <分支名> 创建分支

### git checkout  <分支名> 切换分支

### git checkout -b <分支名> 创建并切换分支

### git merge <分支名> 合并代码

### git merge --no-ff (no fast-forward merge 强行关闭fast-forward方式)

### git merge --squash 分支名 (git中将多次commit合并为一次commit)

### git stash(“‘储藏”“可以获取你工作目录的中间状态——也就是你修改过的被追踪的文件和暂存的变更——并将它保存到一个未完结变更的堆栈中，随时可以重新应用)
    应用场景：假如你现在再并行两个项目，一个是开发阶段，另一个是测试阶段，开发阶段的项目是再A分支，测试阶段的分支是B分支。你在A分支上开发到一半时测试提出bug，这时你需要切换到B分支上去修改，但切换到B分支的时候会把你A分支上修改的代码带过去，而你此时并不想 commit A分支的代码来产生多余的commit记录，这时git stash 就派上用场了。
    
    git stash: 直接git stash 的话 git 会给你一个hash值作为一个版本信息
    git stash save '推荐方式': git 会将 '推荐方式' 作为此次的版本信息
    
    git stash list: 查看现有的储藏
    
    git stash apply stash@{n}: 根据版本信息回到保存的版本
    
    git stash pop: 将git stash栈中最后一个版本取出来
    


# 快捷键 HotKey
充分考虑了多系统和跨平台操作逻辑的一致性的。也就是说 Ctrl、Shift、Alt 这三个键在 Windows、Mac、Linux 不同系统上，还有不同软件上的操作逻辑是相同的。

注意！！本例中涉及到了表单，表格，按钮，弹窗类的一些api, 因此在阅读此文档之前需要对表单，表格，按钮的方法有所了解
 ## 1. 使用场景说明
设计键位时应该充分考虑到：
1.尽量少覆盖修改系统快捷键，这样可以有更好的逻辑性和系统一致性；
2.尽量不改动原始热键功能的情况下去作修改。Alt键作了充分设置，也有达到类似ctrl的组合功能；
3.尽量避免减轻记忆负担，功能互斥按钮，主键字母一样，用Ctrl和Alt区分；
4.尽量单手操作，两个个键位组合，键位选取 "T、G、B" 左侧字母。

 ## 2. 能力特性

 ## 代码演示

 ## 3. API

### 3.1 参数

createButtonApp(id, {config}) 时传入的参数

|参数|说明|类型|默认值|
|:---|:-----|:----|:------|
| id | 模板id | String | 必填 |
| config | 按钮区的参数字典 | Object | 必填 |

createButtonApp 与快捷键相关的 config  ***参数说明***

|参数|说明|类型|默认值|备注|
|:---|:-----|:----|:------|:------|
| ignoreHotkeyCode | 按钮的快捷键相同时不需要触发快捷键的按钮的key| array | [] | 无|
| notInterruptCode | 由按钮的key组成，快捷键不触发当前活跃元素的失焦事件 | array | [] | 无 |
| tabindex | 按钮是否可聚焦 | number | -1(不可聚焦) | 无 |
| modalRelation | 当页面中按钮的快捷键与弹窗里按钮的快捷键相同时需要传入创建弹窗的ID | string | '' | 无|
| hotKeysEnabled | 开关，是否启用快捷键 | boolean | true | 无 |
| tipKeybodard | 快捷键提示模式(underline/none) | string | 'none' | 无 |

### 3.2
createPage(config)(ReactComponent)时需要传入的参数

|参数|说明|类型|默认值|
|:---|:-----|:----|:------|
| config | 参数字典 | object | {} |
| ReactComponent | React 组件 | ReactNode | 必填 |

createPage 与快捷键相关的 config  ***参数说明***

|参数|说明|类型|默认值|备注|
|:---|:-----|:----|:------|:------|
| orderOfHotKey | 页面区域展示顺序,由区域ID组成 | array | [] | 无 |
| appAutoFocus | 默认聚焦到document.body上 | boolean | true | 无|



### 3.3 页面级快捷键api

### 3.3.1 controlAutoFocus

***调用样例 :*** controlAutoFocus(flag)

***说明 :*** 控制页面首项聚焦

***参数说明***:

|参数|说明|类型|默认值|备注|
|:---|:-----|:----|:------|:------|
| flag | 控制页面是否自动聚焦到第一个可编辑项| boolean | true| 无 |

***返回值说明 ：*** 返回undefined 

### 3.3.2 executeAutoFocus

***调用样例 :*** executeAutoFocus()

***说明 :*** 执行页面首项聚焦方法

***返回值说明 ：*** 返回undefined 

### 3.3.3 findFocusModuleId

***调用样例 :*** findFocusModuleId()

***说明 :*** 返回当前焦点属于哪个区域

***备注 :*** 此方法需要在createPage时配置orderOfHotKey才可正常使用

***返回值说明 ：*** 返回当前焦点所属的区域ID 类型为string，如果没有找到返回null


## 4 模板结构

按钮类

|属性|说明|类型|备注|
|:---|:-----|:----|:------|
|keyboard|需要配置的快捷键|string| 无 |
|pageareacode|如果在页面的多个区域中注册了相同的快捷键，比如在表格区域按钮注册了'alt+s'键，表单区域也注册了'alt+s'，此时需要 配置区域ID,当焦点属于该区域时才会触发按钮事件（提示：此属性需要与createPage的orderOfHotKey配合使用）| string | 无


## 5 快捷键键位规则
规范网站拆分成3组快捷键
附件链接：<a href="download/规范网站使用-NCC1909快捷键-Enter版 0828.xlsx">地址</a>

## 5.1 平台快捷键

<table border="2" cellspacing="0">
<tbody><tr><th bgcolor="#B0B0B0" width="30">&nbsp;</th>
  <th align="center" valign="bottom" bgcolor="#B0B0B0" width="150"><b>A</b></th>
  <th align="center" valign="bottom" bgcolor="#B0B0B0" width="432"><b>B</b></th>
  <th align="center" valign="bottom" bgcolor="#B0B0B0" width="653"><b>C</b></th>
  <th align="center" valign="bottom" bgcolor="#B0B0B0" width="631"><b>D</b></th></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="101"><b>1</b></th>
  <td bgcolor="#E2EEDA" colspan="4"></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>2</b></th>
  <td align="center" bgcolor="#E2EEDA" width="120"><font size="3" face="微软雅黑">按键</font></td>
  <td align="center" bgcolor="#E2EEDA" width="346"><font size="3" face="Microsoft YaHei">功能</font></td>
  <td align="center" bgcolor="#E2EEDA" width="523"><font size="3" face="微软雅黑">说明</font></td>
  <td align="center" bgcolor="#E2EEDA" width="505"><font size="3" face="微软雅黑">场景</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="30"><b>3</b></th>
  <td width="120"><font size="3" face="Microsoft YaHei">一、表单、表格中控件的前后切换，4种类型控件的具体按键操作：</font></td>
  <td bgcolor="#D8D8D8" width="346">&nbsp;</td>
  <td bgcolor="#D8D8D8" width="523">&nbsp;</td>
  <td bgcolor="#D8D8D8" width="505">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="38"><b>4&nbsp;</b></th>
  <td width="120" rowspan="3"><font size="3" face="微软雅黑">Tab</font></td>
  <td width="346" rowspan="2"><font size="3" face="微软雅黑">焦点在不同控件间正向移动（从左至右，从上至下）</font></td>
  <td width="523"><font size="3" face="微软雅黑">焦点在上一区域最后一个控件上时，默认跳到下一区域的第一个可编辑或可选择控件上</font></td>
  <td width="505" rowspan="3"><font size="3" face="微软雅黑">1表头最后一个可编辑字段，跳到表体第一个可编辑字段；&nbsp;<br>
  2分组/子表收起时，Teb跳过分组内字段，直接到下一个展开的分组/子表；&nbsp;<br>
  3整表编辑表格的连续新增录入，横向跳转到屏幕外，滚动条随光标翻动；&nbsp;<br>
  4编辑态子表，焦点在表体最后一行时自动增行。</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>5</b></th>
  <td width="523"><font size="3" face="微软雅黑">跳转到折叠区域标题，按空格打开，不空格继续按tab，继续往下跳</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="27"><b>6</b></th>
  <td width="346"><font size="3" face="微软雅黑">录入时，焦点在表格单元格间正向移动</font></td>
  <td width="523"><font size="3" face="微软雅黑">焦点在表体最后一行时，自动增行</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="38"><b>7</b></th>
  <td width="120" rowspan="2"><font size="3" face="微软雅黑">Shift+Tab</font></td>
  <td width="346"><font size="3" face="微软雅黑">焦点在不同控件间逆向移动（从左至右，从上至下）</font></td>
  <td width="523"><font size="3" face="微软雅黑">焦点在下一区域最第一个控件上时，默认跳到上一区域的最后一个可编辑或可选择控件上</font></td>
  <td width="505" rowspan="2"><font size="3" face="微软雅黑">同上，但跳转顺序相反</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>8</b></th>
  <td width="346"><font size="3" face="微软雅黑">录入时，焦点在表格单元格的逆向移动</font></td>
  <td width="523"><font size="3" face="微软雅黑">同上</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>9</b></th>
  <td width="120" rowspan="3"><font size="3" face="微软雅黑">Esc</font></td>
  <td width="346" rowspan="3"><font size="3" face="微软雅黑">取消、退出</font></td>
  <td width="523"><font size="3" face="微软雅黑">下拉菜单操作时退出当前菜单操作，返回上一层</font></td>
  <td width="505" rowspan="3"><font size="3" face="微软雅黑">下拉选项、参照控件的历史记录/已选内容。</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>10</b></th>
  <td width="523"><font size="3" face="微软雅黑">右上提示消息：成功、预警、报错的快速隐藏</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>11</b></th>
  <td width="523"><font size="3" face="微软雅黑">在对话框界面表示什么也不做，相当于取消当前操作，关闭对话框</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>12</b></th>
  <td width="120"><font size="3" face="微软雅黑">←</font></td>
  <td width="346"><font size="3" face="微软雅黑">焦点变光标时，在控件中左移</font></td>
  <td width="523"><font size="3" face="微软雅黑">文本型录入框，光标的控制</font></td>
  <td width="505" rowspan="6"><font size="3" face="微软雅黑">1文本录入中，光标的上下左右控制；&nbsp;<br>
  2下拉菜单中，上下切换待选内容。</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>13</b></th>
  <td width="120"><font size="3" face="微软雅黑">→</font></td>
  <td width="346"><font size="3" face="微软雅黑">焦点变光标时，在控件中右移</font></td>
  <td width="523"><font size="3" face="微软雅黑">文本型录入框，光标的控制</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>14</b></th>
  <td width="120" rowspan="2"><font size="3" face="微软雅黑">↑</font></td>
  <td width="346"><font size="3" face="微软雅黑">在多行文本中光标上移</font></td>
  <td width="523"><font size="3" face="微软雅黑">文本型录入框，光标的控制</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="18"><b>15</b></th>
  <td width="346"><font size="3" face="微软雅黑">焦点在子菜单、下拉列表、表格单元格中上移</font></td>
  <td width="523"><font size="3" face="微软雅黑">下拉菜单中选中项向上移动</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>16</b></th>
  <td width="120" rowspan="2"><font size="3" face="微软雅黑">↓</font></td>
  <td width="346"><font size="3" face="微软雅黑">在多行文本中光标下移</font></td>
  <td width="523"><font size="3" face="微软雅黑">文本型录入框，光标的控制</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="18"><b>17</b></th>
  <td width="346"><font size="3" face="微软雅黑">焦点在子菜单、下拉列表、表格单元格中下移</font></td>
  <td width="523"><font size="3" face="微软雅黑">下拉菜单中选中项向下移动</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="36"><b>18</b></th>
  <td width="120"><font size="3" face="微软雅黑">F1</font></td>
  <td width="346"><font size="3" face="微软雅黑">打开快捷键帮助文档</font></td>
  <td width="523">&nbsp;</td>
  <td width="505">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>19</b></th>
  <td width="120" rowspan="2"><font size="3" face="微软雅黑">F2</font></td>
  <td width="346"><font size="3" face="Microsoft YaHei">打开光标所在日期控件面板</font></td>
  <td width="523" rowspan="2"><font size="3" face="微软雅黑">打开参照/日期面板</font></td>
  <td width="505" rowspan="2"><font size="3" face="微软雅黑">参照、日期、公式计算</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>20</b></th>
  <td width="346"><font size="3" face="微软雅黑">打开光标所在位置的参照对话框</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="18"><b>21</b></th>
  <td width="120"><font size="3" face="Microsoft YaHei">空格键 </font></td>
  <td width="346"><font size="3" face="Microsoft YaHei">展开/收起</font></td>
  <td width="523"><font size="3" face="Microsoft YaHei">展开状态执行收起，收起状态执行展开</font></td>
  <td width="505"><font size="3" face="Microsoft YaHei">控制单据分组信息的展开或收起；</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="18"><b>22</b></th>
  <td width="120" rowspan="4"><font size="3" face="微软雅黑">Enter</font></td>
  <td width="346" rowspan="3"><font size="3" face="微软雅黑">确认</font></td>
  <td width="523" rowspan="3"><font size="3" face="微软雅黑">对话框或信息框确定焦点所在按钮</font></td>
  <td width="505" rowspan="3"><font size="3" face="微软雅黑">1下拉菜单的确定选中和切换下一个；&nbsp;<br>
  2对话框的确定类操作；&nbsp;<br>
  3确认选中并跳到下一个。</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="18"><b>23</b></th></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>24</b></th></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>25</b></th>
  <td width="346"><font size="3" face="微软雅黑">页面切换</font></td>
  <td width="523"><font size="3" face="微软雅黑">浏览态，从列表界面切换到卡片界面</font></td>
  <td width="505"><font size="3" face="微软雅黑">进入已选列表的详情</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>26</b></th>
  <td width="120" rowspan="2"><font size="3" face="微软雅黑">Del </font></td>
  <td width="346" rowspan="2"><font size="3" face="微软雅黑">删除键</font></td>
  <td width="523"><font size="3" face="微软雅黑">删除光标后一个字符</font></td>
  <td width="505"><font size="3" face="微软雅黑">文本、数值录入框</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="30"><b>27</b></th>
  <td width="523"><font size="3" face="微软雅黑">移除当前选中的输入项目</font></td>
  <td width="505"><font size="3" face="微软雅黑">参照、多选参照的已选内容</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="30"><b>28</b></th>
  <td width="120" rowspan="2"><font size="3" face="微软雅黑">Pageup</font></td>
  <td width="346" rowspan="2"><font size="3" face="微软雅黑">向上整页滚动</font></td>
  <td width="523"><font size="3" face="微软雅黑">页面整屏向上翻动一页</font></td>
  <td width="505" rowspan="4"><font size="3" face="微软雅黑">1内容超过当前页面；&nbsp;<br>
  2单据子表内容翻页；&nbsp;<br>
  3参照树、内容。。。。。。</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="30"><b>29</b></th>
  <td width="523"><font size="3" face="微软雅黑">参照</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="30"><b>30</b></th>
  <td width="120" rowspan="2"><font size="3" face="微软雅黑">Pagedown</font></td>
  <td width="346" rowspan="2"><font size="3" face="微软雅黑">向下整页滚动</font></td>
  <td width="523"><font size="3" face="微软雅黑">页面整屏向下翻动一页</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="30"><b>31</b></th>
  <td width="523"><font size="3" face="微软雅黑">参照</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="30"><b>32</b></th>
  <td width="120"><font size="3" face="微软雅黑">Alt+←</font></td>
  <td width="346"><font size="3" face="微软雅黑">向左整页滚动</font></td>
  <td width="523"><font size="3" face="微软雅黑">列表浏览态向左翻动一页</font></td>
  <td width="505" rowspan="4"><font size="3" face="微软雅黑">1参照待选列表；&nbsp;<br>
  2参照树结构。。。。。。</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="30"><b>33</b></th>
  <td width="120"><font size="3" face="微软雅黑">Alt+→</font></td>
  <td width="346"><font size="3" face="微软雅黑">向右整页滚动</font></td>
  <td width="523"><font size="3" face="微软雅黑">列表浏览态向左翻动一页</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="30"><b>34</b></th>
  <td width="120"><font size="3" face="微软雅黑">Alt+↑</font></td>
  <td width="346"><font size="3" face="微软雅黑">向上整页滚动</font></td>
  <td width="523"><font size="3" face="微软雅黑">列表浏览态向左翻动一页</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="30"><b>35</b></th>
  <td width="120"><font size="3" face="微软雅黑">Alt+↓</font></td>
  <td width="346"><font size="3" face="微软雅黑">向下整页滚动</font></td>
  <td width="523"><font size="3" face="微软雅黑">列表浏览态向左翻动一页</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="27"><b>36</b></th>
  <td bgcolor="#D8D8D8" colspan="4"><font size="3" face="微软雅黑">二、NCC 
  采用外部页签，如下快捷键非常实用，浏览器和系统快捷键不要受干扰：</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>37</b></th>
  <td width="120"><font size="3" face="微软雅黑">Ctrl+Tab</font></td>
  <td width="346"><font size="3" face="微软雅黑">切换到下一个标签页。</font></td>
  <td width="523" rowspan="4"><font size="3" face="微软雅黑">NC Cloud采用外部页签管理内容，需要快捷操作控制浏览器页签</font></td>
  <td width="505" rowspan="13"><font size="3" face="微软雅黑">1通用快捷键，Chrome、IE、Linux均能使用；&nbsp;<br>
  2快捷切换、开启/关闭外部页签，方便管理；&nbsp;<br>
  3定位页面内容，顶部、底部、逐页翻页。</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>38</b></th>
  <td width="120"><font size="3" face="微软雅黑">Ctrl+Shift+Tab </font></td>
  <td width="346"><font size="3" face="微软雅黑">切换到上一个标签页。</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>39</b></th>
  <td width="120"><font size="3" face="微软雅黑">Ctrl+W </font></td>
  <td width="346"><font size="3" face="微软雅黑">关闭当前标签页或弹出窗口。</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>40</b></th>
  <td width="120"><font size="3" face="微软雅黑">Ctrl+R </font></td>
  <td width="346"><font size="3" face="微软雅黑">重新载入当前网页。</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>41</b></th>
  <td width="120"><font size="3" face="Microsoft YaHei"><b><s><strike>空格键 </strike></s></b></font></td>
  <td width="346"><font size="3" face="Microsoft YaHei"><b><s><strike>向下滚动网页(删除)</strike></s></b></font></td>
  <td width="523" rowspan="3"><font size="3" face="微软雅黑">大量数据例如维护单，快速定位到顶/底部和向下翻页</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>42</b></th>
  <td width="120"><font size="3" face="微软雅黑">Home </font></td>
  <td width="346"><font size="3" face="微软雅黑">转至网页顶部。</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>43</b></th>
  <td width="120"><font size="3" face="微软雅黑">End </font></td>
  <td width="346"><font size="3" face="微软雅黑">转至网页底部。</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>44</b></th>
  <td width="120"><font size="3" face="微软雅黑">Ctrl++ </font></td>
  <td width="346"><font size="3" face="微软雅黑">放大网页上的所有内容。</font></td>
  <td width="523" rowspan="3"><font size="3" face="微软雅黑">视觉设计师推荐快速放大/缩小网页内容，便于阅读</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>45</b></th>
  <td width="120"><font size="3" face="微软雅黑">Ctrl+- </font></td>
  <td width="346"><font size="3" face="微软雅黑">缩小网页上的所有内容。</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>46</b></th>
  <td width="120"><font size="3" face="微软雅黑">Ctrl+0 </font></td>
  <td width="346"><font size="3" face="微软雅黑">将网页上内容都恢复到正常大小。</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>47</b></th>
  <td width="120"><font size="3" face="微软雅黑">Ctrl+F </font></td>
  <td width="346"><font size="3" face="微软雅黑">打开查找栏。</font></td>
  <td width="523" rowspan="3"><font size="3" face="微软雅黑">快速定位查找的内容</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="22"><b>48</b></th>
  <td width="120"><font size="3" face="微软雅黑">Ctrl+←</font></td>
  <td width="346"><font size="3" face="微软雅黑">浏览记录后退</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="22"><b>49</b></th>
  <td width="120"><font size="3" face="微软雅黑">Ctrl+→</font></td>
  <td width="346"><font size="3" face="微软雅黑">浏览记录前进</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="18"><b>50</b></th>
  <td bgcolor="#D8D8D8" colspan="4"><font size="3" face="Microsoft YaHei">三、NCC时间控件快捷键</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>51</b></th>
  <td width="120"><font size="3" face="微软雅黑">→</font></td>
  <td width="346"><font size="3" face="DengXian">焦点从开始日期跳到结束日期。焦点在日期数字区域或函数区域按天正向移动。</font></td>
  <td width="523"><font size="3" face="DengXian">光标如果在起始日期数字末尾，“右”可跳到结束时间录入区。</font></td>
  <td width="505" rowspan="7"><font size="3" face="DengXian">含时间控件的场景</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>52</b></th>
  <td width="120"><font size="3" face="微软雅黑">←</font></td>
  <td width="346"><font size="3" face="DengXian">焦点从结束日期跳到开始日期。焦点在日期数字区域或函数区域按天反向移动。</font></td>
  <td width="523"><font size="3" face="DengXian">光标如果在结束日期数字首位，“左”可跳到开始时间录入区。 </font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>
  53</b></th>
  <td width="120"><font size="3" face="微软雅黑">↑</font></td>
  <td width="346"><font size="3" face="DengXian">焦点在日期数字区域或函数区域按行向上移动。</font></td>
  <td width="523">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>54</b></th>
  <td width="120"><font size="3" face="Microsoft YaHei">↓</font></td>
  <td width="346"><font size="3" face="DengXian">a 焦点在日期控件录入框内时，按“下”触发面板，焦点落在开始时间区域。&nbsp;<br>
  b 焦点在日期数字区域或函数区域按行向下移动。</font></td>
  <td width="523">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>55</b></th>
  <td width="120"><font size="3" face="Microsoft YaHei">Tab</font></td>
  <td width="346"><font size="3" face="DengXian">a 上一个控件tab到日期控件内，不触发时间面板&nbsp;<br>
  b 焦点在录入区域、日期数字区域、函数区域循环移动。</font></td>
  <td width="523">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>56</b></th>
  <td width="120"><font size="3" face="DengXian">Enter</font></td>
  <td width="346"><font size="3" face="DengXian">选中开始日期，选中结束日期并收起。</font></td>
  <td width="523"><font size="3" face="DengXian">a&nbsp; 区间：选中结束日期并收起面板，焦点落在下一个可录入控件内。&nbsp;<br>
  b 单选日期：选中并收起面板，焦点落在下一个可录入空间内。</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>57</b></th>
  <td width="120"><font size="3" face="DengXian">Esc</font></td>
  <td width="346"><font size="3" face="DengXian">收起时间面板。焦点落在当前控件内。</font></td>
  <td width="523">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>58</b></th>
  <td bgcolor="#D8D8D8" colspan="4"><font size="3" face="Microsoft YaHei">四、查询区快捷键</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>59</b></th>
  <td width="120"><font size="3" face="微软雅黑">Enter</font></td>
  <td width="346"><font size="3" face="DengXian">执行查询</font></td>
  <td width="523">&nbsp;</td>
  <td width="505">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>60</b></th>
  <td width="120"><font size="3" face="Microsoft YaHei">F3</font></td>
  <td width="346"><font size="3" face="DengXian">展开高级面板</font></td>
  <td width="523">&nbsp;</td>
  <td width="505">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>61&nbsp;</b></th>
  <td width="120"><font size="3" face="Microsoft YaHei">Alt+Del</font></td>
  <td width="346"><font size="3" face="DengXian">清空查询条件</font></td>
  <td width="523">&nbsp;</td>
  <td width="505">&nbsp;</td></tr>
</tbody></table>


## 5.2 公共快捷键

<table border="2" cellspacing="0">
<tbody><tr><th bgcolor="#B0B0B0" width="30">&nbsp;</th>
  <th align="center" valign="bottom" bgcolor="#B0B0B0" width="185"><b>A&nbsp;</b></th>
  <th align="center" valign="bottom" bgcolor="#B0B0B0" width="198"><b>B&nbsp;</b></th>
  <th align="center" valign="bottom" bgcolor="#B0B0B0" width="158"><b>C&nbsp;</b></th>
  <th align="center" valign="bottom" bgcolor="#B0B0B0" width="623"><b>D&nbsp;</b></th>
  <th align="center" valign="bottom" bgcolor="#B0B0B0" width="410"><b>E&nbsp;</b></th></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="95"><b>1&nbsp;</b></th>
  <td bgcolor="#E2EEDA" colspan="5"><font size="3" face="微软雅黑">&nbsp;&nbsp;&nbsp; 
  平台已经给各领域留好注册接口，例如：供应链入库单“货位序列号”、存量查检“采购询价”按钮，产品组各自添加注册，但是要从UE处输出。按键组合基于以下：&nbsp;<br>
  &nbsp;&nbsp;&nbsp; 1.Ctrl 是 Control 的缩写，意思是“控制”。Ctrl 
  键用来执行命令的，大部分的快捷键都与它相关。&nbsp;<br>
  &nbsp;&nbsp;&nbsp; 2.Alt 是 Alter 的缩写，是“改变”的意思。Alt 
  键与菜单相关，更进一步说，Alt 键与图形用户界面（GUI）相关，也就是与窗口相关。&nbsp;<br>
  &nbsp;&nbsp;&nbsp; 3.Shift 的意思是“切换”。所以Shift 键就是对原有功能的切换，比如按住 
  Shift 键切换到大写。&nbsp;<br>
  &nbsp;&nbsp;&nbsp; 4.F1-12 是 Function.即功能键。在DOS时代是功能键，比如重复刚使用过的命令行，启动BIOS之类的。</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="25"><b>2</b></th>
  <td bgcolor="#E2EEDA" colspan="5"><font size="3" face="Microsoft YaHei">备注：Del、Ins需要简写</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>3</b></th>
  <td align="center" bgcolor="#E2EEDA" width="148"><font size="3" face="微软雅黑">区域</font></td>
  <td align="center" bgcolor="#E2EEDA" width="159"><font size="3" face="微软雅黑">操作</font></td>
  <td align="center" bgcolor="#E2EEDA" width="127"><font size="3" face="Microsoft YaHei">快捷键</font></td>
  <td align="center" bgcolor="#E2EEDA" width="499"><font size="3" face="微软雅黑">说明</font></td>
  <td align="center" bgcolor="#E2EEDA" width="328"><font size="3" face="微软雅黑">来源</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="18"><b>4</b></th>
  <td bgcolor="#D8D8D8" colspan="5"><font size="3" face="微软雅黑">一、表单、表格中控件的前后切换，4种类型控件的具体按键操作：</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="18"><b>5</b></th>
  <td width="148" rowspan="10"><font size="3" face="微软雅黑">单据编辑态</font></td>
  <td width="159"><font size="3" face="微软雅黑">快捷键帮助</font></td>
  <td width="127"><font size="3" face="微软雅黑">F3</font></td>
  <td width="499"><font size="3" face="微软雅黑">查看快捷键帮助文档</font></td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="18"><b>6</b></th>
  <td width="159"><font size="3" face="微软雅黑">保存</font></td>
  <td width="127"><font size="3" face="微软雅黑">Ctrl+S</font></td>
  <td width="499"><font size="3" face="微软雅黑">与浏览器键位冲突。不是常用快捷键，功能可以被右键替代</font></td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>7</b></th>
  <td width="159"><font size="3" face="微软雅黑">保存并新增</font></td>
  <td width="127"><font size="3" face="微软雅黑">Alt+S</font></td>
  <td width="499">&nbsp;</td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>8</b></th>
  <td width="159"><font size="3" face="微软雅黑">保存并提交</font></td>
  <td width="127"><font size="3" face="微软雅黑">Alt+T</font></td>
  <td width="499">&nbsp;</td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>9</b></th>
  <td width="159"><font size="3" face="微软雅黑">取消</font></td>
  <td width="127"><font size="3" face="微软雅黑">Alt+Q</font></td>
  <td width="499">&nbsp;</td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>10</b></th>
  <td width="159"><font size="3" face="微软雅黑">暂存</font></td>
  <td width="127"><font size="3" face="微软雅黑">Ctrl+Alt+S</font></td>
  <td width="499">&nbsp;</td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>11</b></th>
  <td width="159"><font size="3" face="微软雅黑">向左跳动</font></td>
  <td width="127"><font size="3" face="微软雅黑">Shift+←</font></td>
  <td width="499" rowspan="2"><font size="3" face="微软雅黑">单据子表页签，左右切换</font></td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>12</b></th>
  <td width="159"><font size="3" face="微软雅黑">向右跳动</font></td>
  <td width="127"><font size="3" face="微软雅黑">Shift+→</font></td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>13</b></th>
  <td width="159"><font size="3" face="微软雅黑">向上跳动</font></td>
  <td width="127"><font size="3" face="微软雅黑">Shift+↑</font></td>
  <td width="499" rowspan="2"><font size="3" face="微软雅黑">单据分组、子表，上下切换</font></td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>14</b></th>
  <td width="159"><font size="3" face="微软雅黑">向下跳动</font></td>
  <td width="127"><font size="3" face="微软雅黑">Shift+↓</font></td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>15</b></th>
  <td width="148" rowspan="9"><font size="3" face="Microsoft YaHei">单据编辑态-子表</font></td>
  <td width="159"><font size="3" face="微软雅黑">增行</font></td>
  <td width="127"><font size="3" face="微软雅黑">Alt+N</font></td>
  <td width="499"><font size="3" face="微软雅黑">应用在子表肩部按钮</font></td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="38"><b>16</b></th>
  <td width="159"><font size="3" face="微软雅黑">删行</font></td>
  <td width="127"><font size="3" face="Microsoft YaHei">Alt+Backspace&nbsp;<br>
  Alt+Del</font></td>
  <td width="499" rowspan="6"><font size="3" face="微软雅黑">应用在子表行按钮</font></td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>17</b></th>
  <td width="159"><font size="3" face="Microsoft YaHei">插行</font></td>
  <td width="127"><font size="3" face="微软雅黑">Alt+I</font></td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>18</b></th>
  <td width="159"><font size="3" face="微软雅黑">复制行</font></td>
  <td width="127"><font size="3" face="微软雅黑">Alt+C</font></td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>19</b></th>
  <td width="159"><font size="3" face="微软雅黑">粘贴行</font></td>
  <td width="127"><font size="3" face="微软雅黑">Alt+V</font></td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>20</b></th>
  <td width="159"><font size="3" face="微软雅黑">粘贴到末行</font></td>
  <td width="127"><font size="3" face="微软雅黑">Ctrl+Alt+V</font></td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>21</b></th>
  <td width="159"><font size="3" face="Microsoft YaHei">展开/收起侧边弹窗</font></td>
  <td width="127"><font size="3" face="微软雅黑">F4</font></td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>22</b></th>
  <td width="159"><font size="3" face="微软雅黑">批改</font></td>
  <td width="127"><font size="3" face="微软雅黑">Alt+P</font></td>
  <td width="499">&nbsp;</td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>23</b></th>
  <td width="159"><font size="3" face="微软雅黑">重排序号/行号</font></td>
  <td width="127"><font size="3" face="微软雅黑">Alt+R</font></td>
  <td width="499">&nbsp;</td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>24</b></th>
  <td width="148" rowspan="12"><font size="3" face="微软雅黑">单据浏览态 
  或&nbsp;<br>
  &nbsp;<br>
  列表基础按钮</font></td>
  <td width="159"><font size="3" face="微软雅黑">新增</font></td>
  <td width="127"><font size="3" face="微软雅黑">Ctrl+/</font></td>
  <td width="499">&nbsp;</td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>25</b></th>
  <td width="159"><font size="3" face="微软雅黑">自制</font></td>
  <td width="127"><font size="3" face="微软雅黑">Ctrl+/</font></td>
  <td width="499">&nbsp;</td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>26</b></th>
  <td width="159"><font size="3" face="微软雅黑">修改</font></td>
  <td width="127"><font size="3" face="微软雅黑">Alt+P</font></td>
  <td width="499">&nbsp;</td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="37"><b>27</b></th>
  <td width="159"><font size="3" face="微软雅黑">删除</font></td>
  <td width="127"><font size="3" face="Microsoft YaHei">Ctrl+Backspace&nbsp;<br>
  Ctrl+Del</font></td>
  <td width="499">&nbsp;</td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>28</b></th>
  <td width="159"><font size="3" face="微软雅黑">复制</font></td>
  <td width="127"><font size="3" face="微软雅黑">Alt+C</font></td>
  <td width="499">&nbsp;</td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>29</b></th>
  <td width="159"><font size="3" face="微软雅黑">提交</font></td>
  <td width="127"><font size="3" face="微软雅黑">Alt+B</font></td>
  <td width="499">&nbsp;</td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>30</b></th>
  <td width="159"><font size="3" face="微软雅黑">收回</font></td>
  <td width="127"><font size="3" face="微软雅黑">Ctrl+B</font></td>
  <td width="499">&nbsp;</td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>31</b></th>
  <td width="159"><font size="3" face="微软雅黑">变更</font></td>
  <td width="127"><font size="3" face="微软雅黑">Alt+R</font></td>
  <td width="499">&nbsp;</td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>32</b></th>
  <td width="159"><font size="3" face="微软雅黑">返回</font></td>
  <td width="127"><font size="3" face="微软雅黑">Shift+Esc</font></td>
  <td width="499">&nbsp;</td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>33</b></th>
  <td width="159"><font size="3" face="微软雅黑">前一页</font></td>
  <td width="127"><font size="3" face="微软雅黑">Alt+Pageup</font></td>
  <td width="499">&nbsp;</td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>34</b></th>
  <td width="159"><font size="3" face="微软雅黑">后一页</font></td>
  <td width="127"><font size="3" face="微软雅黑">Alt+Pagedown</font></td>
  <td width="499">&nbsp;</td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>35</b></th>
  <td width="159"><font size="3" face="微软雅黑">刷新</font></td>
  <td width="127"><font size="3" face="微软雅黑">F5</font></td>
  <td width="499">&nbsp;</td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>36</b></th>
  <td align="center" width="148" rowspan="18"><font size="3" face="Microsoft YaHei">列表肩部按钮</font></td>
  <td width="159"><font size="3" face="微软雅黑">签字</font></td>
  <td width="127"><font size="3" face="微软雅黑">Ctrl+I</font></td>
  <td width="499">&nbsp;</td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>37</b></th>
  <td width="159"><font size="3" face="微软雅黑">取消签字</font></td>
  <td width="127"><font size="3" face="微软雅黑">Alt+I</font></td>
  <td width="499">&nbsp;</td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>38</b></th>
  <td width="159"><font size="3" face="微软雅黑">审批</font></td>
  <td width="127"><font size="3" face="微软雅黑">Ctrl+U</font></td>
  <td width="499">&nbsp;</td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>39</b></th>
  <td width="159"><font size="3" face="微软雅黑">取消审批</font></td>
  <td width="127"><font size="3" face="微软雅黑">Alt+U</font></td>
  <td width="499">&nbsp;</td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>40</b></th>
  <td width="159"><font size="3" face="微软雅黑">作废</font></td>
  <td width="127"><font size="3" face="微软雅黑">Ctrl+G</font></td>
  <td width="499">&nbsp;</td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>41</b></th>
  <td width="159"><font size="3" face="微软雅黑">取消作废</font></td>
  <td width="127"><font size="3" face="微软雅黑">Alt+G</font></td>
  <td width="499">&nbsp;</td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>42</b></th>
  <td width="159"><font size="3" face="微软雅黑">冻结</font></td>
  <td width="127"><font size="3" face="微软雅黑">Ctrl+J</font></td>
  <td width="499">&nbsp;</td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>43</b></th>
  <td width="159"><font size="3" face="微软雅黑">取消冻结</font></td>
  <td width="127"><font size="3" face="微软雅黑">Alt+J</font></td>
  <td width="499">&nbsp;</td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>44</b></th>
  <td width="159"><font size="3" face="微软雅黑">结账</font></td>
  <td width="127"><font size="3" face="微软雅黑">Ctrl+J</font></td>
  <td width="499">&nbsp;</td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>45</b></th>
  <td width="159"><font size="3" face="微软雅黑">取消结账</font></td>
  <td width="127"><font size="3" face="微软雅黑">Alt+J</font></td>
  <td width="499">&nbsp;</td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>46</b></th>
  <td width="159"><font size="3" face="微软雅黑">导入</font></td>
  <td width="127"><font size="3" face="微软雅黑">Ctrl+Alt+E</font></td>
  <td width="499">&nbsp;</td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>47</b></th>
  <td width="159"><font size="3" face="微软雅黑">导出</font></td>
  <td width="127"><font size="3" face="微软雅黑">Ctrl+Alt+C</font></td>
  <td width="499">&nbsp;</td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>48</b></th>
  <td width="159"><font size="3" face="微软雅黑">打印</font></td>
  <td width="127"><font size="3" face="微软雅黑">Ctrl+P</font></td>
  <td width="499"><font size="3" face="微软雅黑">与浏览器键位冲突。不是常用快捷键，功能可以被右键替代</font></td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>49</b></th>
  <td width="159"><font size="3" face="微软雅黑">联查-联查单据</font></td>
  <td width="127"><font size="3" face="微软雅黑">Ctrl+K</font></td>
  <td width="499">&nbsp;</td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>50</b></th>
  <td width="159"><font size="3" face="微软雅黑">联查-审批流程</font></td>
  <td width="127"><font size="3" face="Microsoft YaHei">Ctrl+O</font></td>
  <td width="499"><font size="3" face="Microsoft YaHei">流程审批，Ctrl+O。打开流程审批一级菜单。</font></td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>51</b></th>
  <td width="159"><font size="3" face="微软雅黑">收款</font></td>
  <td width="127"><font size="3" face="微软雅黑">Alt+O</font></td>
  <td width="499">&nbsp;</td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>52</b></th>
  <td width="159"><font size="3" face="微软雅黑">附件管理</font></td>
  <td width="127"><font size="3" face="微软雅黑">Alt+D</font></td>
  <td width="499"><font size="3" face="微软雅黑">与浏览器键位冲突。不是常用快捷键，功能可以被右键替代</font></td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>53</b></th>
  <td width="159"><font size="3" face="微软雅黑">记账、纠错</font></td>
  <td width="127"><font size="3" face="微软雅黑">Alt+L</font></td>
  <td width="499">&nbsp;</td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>54</b></th>
  <td width="148" rowspan="4"><font size="3" face="微软雅黑">判断弹窗 
  或&nbsp;<br>
  &nbsp;<br>
  提示信息</font></td>
  <td width="159"><font size="3" face="微软雅黑">确定并关闭弹窗</font></td>
  <td width="127"><font size="3" face="微软雅黑">Alt+Y</font></td>
  <td width="499">&nbsp;</td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="19"><b>55</b></th>
  <td width="159"><font size="3" face="微软雅黑">取消并关闭弹窗</font></td>
  <td width="127"><font size="3" face="微软雅黑">Alt+N</font></td>
  <td width="499">&nbsp;</td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="38"><b>56</b></th>
  <td width="159"><font size="3" face="Microsoft YaHei">确定并关闭弹窗、&nbsp;<br>
  </font></td>
  <td width="127"><font size="3" face="Microsoft YaHei">Enter</font></td>
  <td width="499"><font size="3" face="Microsoft YaHei">提示信息，查看更多内容</font></td>
  <td width="328">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="38"><b>57</b></th>
  <td width="159"><font size="3" face="微软雅黑">取消并关闭弹窗、&nbsp;<br>
  隐藏提示信息</font></td>
  <td width="127"><font size="3" face="微软雅黑">Esc</font></td>
  <td width="499"><font size="3" face="微软雅黑">收起提示信息</font></td>
  <td width="328">&nbsp;</td></tr>
</tbody></table>


## 5.3 参照快捷键

<table border="2" cellspacing="0">
<tbody><tr><th bgcolor="#B0B0B0" width="30">&nbsp;</th>
  <th align="center" valign="bottom" bgcolor="#B0B0B0" width="103"><b>A</b></th>
  <th align="center" valign="bottom" bgcolor="#B0B0B0" width="300"><b>B</b></th>
  <th align="center" valign="bottom" bgcolor="#B0B0B0" width="453"><b>C</b></th>
  <th align="center" valign="bottom" bgcolor="#B0B0B0" width="437"><b>D</b></th></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="21"><b>1</b></th>
  <td bgcolor="#A9D08E" colspan="4">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>2</b></th>
  <td align="center" bgcolor="#E2EFDA" width="83"><font color="#404040" size="3" face="微软雅黑">按键</font></td>
  <td align="center" bgcolor="#E2EFDA" width="240"><font color="#404040" size="3" face="微软雅黑">功能</font></td>
  <td align="center" bgcolor="#E2EFDA" width="363"><font color="#404040" size="3" face="微软雅黑">说明</font></td>
  <td align="center" bgcolor="#E2EFDA" width="350"><font color="#404040" size="3" face="微软雅黑">场景</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="20"><b>3</b></th>
  <td bgcolor="#D9D9D9" width="83">&nbsp;</td>
  <td bgcolor="#D9D9D9" width="240">&nbsp;</td>
  <td bgcolor="#D9D9D9" width="363">&nbsp;</td>
  <td bgcolor="#D9D9D9" width="350">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>4&nbsp;</b></th>
  <td width="83"><font color="#404040" size="3" face="微软雅黑">tab</font></td>
  <td width="240"><font color="#404040" size="3" face="微软雅黑">tab到参照框中（显示边框色），自动获取焦点、展开最近历史记录</font></td>
  <td width="363"><font color="#404040" size="3" face="微软雅黑">默认未选择字段时</font></td>
  <td width="350" rowspan="6"><font color="#404040" size="3" face="微软雅黑">单选/多选参照框，默认未选择字段时</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>5</b></th>
  <td width="83"><font color="#404040" size="3" face="微软雅黑">↓</font></td>
  <td width="240"><font color="#404040" size="3" face="微软雅黑">向下选择数据</font></td>
  <td width="363"><font color="#404040" size="3" face="微软雅黑">从第一个开始，移动在下拉面板时，数据上有底色</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>6</b></th>
  <td width="83"><font color="#404040" size="3" face="微软雅黑">↑</font></td>
  <td width="240"><font color="#404040" size="3" face="微软雅黑">向上选择数据</font></td>
  <td width="363"><font color="#404040" size="3" face="微软雅黑">配合↓键使用</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>7</b></th>
  <td width="83"><font size="3" face="微软雅黑">enter</font></td>
  <td width="240"><font color="#404040" size="3" face="微软雅黑">确定选择</font></td>
  <td width="363"><font color="#404040" size="3" face="微软雅黑">面板收起，参照框中赋值，且跳到下一个可编辑的录入组件</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>8</b></th>
  <td width="83"><font color="#404040" size="3" face="微软雅黑">←</font></td>
  <td width="240"><font color="#404040" size="3" face="微软雅黑">字符间距向左移动</font></td>
  <td width="363"><font color="#404040" size="3" face="微软雅黑">录入关键字后，左移一个字符</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>9</b></th>
  <td width="83"><font color="#404040" size="3" face="微软雅黑">→</font></td>
  <td width="240"><font color="#404040" size="3" face="微软雅黑">字符间距向右移动</font></td>
  <td width="363"><font color="#404040" size="3" face="微软雅黑">录入关键字后，右移一个字符</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>10</b></th>
  <td width="83"><font color="#404040" size="3" face="微软雅黑">空格</font></td>
  <td width="240"><font color="#404040" size="3" face="微软雅黑">选中/反选</font></td>
  <td width="363">&nbsp;</td>
  <td width="350"><font color="#404040" size="3" face="微软雅黑">多选参照框，默认未选择字段时</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>11</b></th>
  <td width="83"><font color="#404040" size="3" face="微软雅黑">delete</font></td>
  <td width="240"><font color="#404040" size="3" face="微软雅黑">清空</font></td>
  <td width="363"><font color="#404040" size="3" face="微软雅黑">清空所有已选项</font></td>
  <td width="350" rowspan="6"><font color="#404040" size="3" face="微软雅黑">单选/多选参照框，默认存在已选字段时</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>12</b></th>
  <td width="83">&nbsp;</td>
  <td width="240"><font color="#404040" size="3" face="微软雅黑">单个删除</font></td>
  <td width="363"><font size="2" face="Microsoft YaHei">下拉面板展开后，移动到已选数据时点击del即可删除</font><font size="3" face="®oÅÑ">（把最后一个删除时，参照框获取焦点，下拉面板展示历史记录）</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>13</b></th>
  <td width="83"><font color="#404040" size="3" face="微软雅黑">↓</font></td>
  <td width="240"><font color="#404040" size="3" face="微软雅黑">展开已选面板</font></td>
  <td width="363"><font color="#404040" size="3" face="微软雅黑">选中已选参照框时，点击↓显示已选面板（参照框有边框色）</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>14</b></th>
  <td width="83">&nbsp;</td>
  <td width="240"><font color="#404040" size="3" face="微软雅黑">向下选择数据</font></td>
  <td width="363"><font color="#404040" size="3" face="微软雅黑">下拉面板展开后，从第一个开始，移动在下拉面板时，数据上有底色</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>15</b></th>
  <td width="83"><font color="#404040" size="3" face="微软雅黑">↑</font></td>
  <td width="240"><font color="#404040" size="3" face="微软雅黑">向上选择数据</font></td>
  <td width="363"><font color="#404040" size="3" face="微软雅黑">下拉面板展开后，向上移动，直至移动到参照框</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="46"><b>16</b></th>
  <td width="83">&nbsp;</td>
  <td width="240">&nbsp;</td>
  <td width="363"><font size="2" face="Microsoft YaHei">另：若单选参照，后期已选后获取焦点，&nbsp;<br>
  1.tab到已选项时，所选项标蓝色，焦点在最后&nbsp;&nbsp;<br>
  2.按</font><font size="2" face="Microsoft YaHei">←、</font><font size="2" face="Microsoft YaHei">→键所选颜色消失，光标定位最后。</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="20"><b>17</b></th>
  <td width="83">&nbsp;</td>
  <td bgcolor="#D9D9D9" width="240">&nbsp;</td>
  <td bgcolor="#D9D9D9" width="363">&nbsp;</td>
  <td bgcolor="#D9D9D9" width="350">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>18</b></th>
  <td width="83"><font size="3" face="DengXian">F2</font></td>
  <td width="240"><font color="#282828" size="3" face="微软雅黑">打开光标所在位置的参照对话框</font></td>
  <td width="363"><font size="3" face="DengXian">打开面板</font></td>
  <td width="350" rowspan="4"><font color="#404040" size="3" face="微软雅黑">参照面板公共按键</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>19</b></th>
  <td width="83"><font color="#282828" size="3" face="DengXian">alt+Y</font></td>
  <td width="240"><font color="#282828" size="3" face="微软雅黑">确定并关闭参照弹窗</font></td>
  <td width="363">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>20</b></th>
  <td width="83"><font color="#282828" size="3" face="微软雅黑">alt+N</font></td>
  <td width="240"><font size="3" face="微软雅黑">取消并关闭参照弹窗</font></td>
  <td width="363">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>21</b></th>
  <td width="83"><font color="#282828" size="3" face="微软雅黑">esc</font></td>
  <td width="240"><font size="3" face="微软雅黑">关闭</font></td>
  <td width="363">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>22</b></th>
  <td width="83"><font color="#404040" size="3" face="微软雅黑">tab</font></td>
  <td width="240"><font color="#282828" size="3" face="微软雅黑">组件、区域顺序跳转</font></td>
  <td width="363"><font size="2" face="Microsoft YaHei">默认在表的第一条数据，跳转顺序：表的第一条数据（第二次循环时，选中的第一个）、组件（与确定、取消同行的复选框或其他按钮；确定、取消不跳）、业务单元、搜索、搜索右侧的组件、循环&nbsp;<br>
  默认在表的</font><font size="3" face="®oÅÑ">第一条数据，跳转顺序：表的第一条数据（第二次循环时，选中的第一个）、搜索右侧的组件、组件（与确定、取消同行的复选框或其他按钮；确定、取消不跳）、业务单元、搜索、循环</font></td>
  <td width="350" rowspan="5"><font color="#404040" size="3" face="微软雅黑">单选表参照面板</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>23</b></th>
  <td width="83"><font size="3" face="微软雅黑">shift+tab</font></td>
  <td width="240"><font color="#282828" size="3" face="微软雅黑">组件、区域反向顺序跳转</font></td>
  <td width="363"><font color="#282828" size="3" face="微软雅黑">同上，顺序相反</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>24</b></th>
  <td width="83"><font color="#404040" size="3" face="微软雅黑">↓</font></td>
  <td width="240"><font color="#282828" size="3" face="微软雅黑">表中向下移动光标</font></td>
  <td width="363"><font size="2" face="Microsoft YaHei">1.只在数据区域内移动&nbsp;<br>
  2.配合确定完成选择（整表编辑时：点击“确定”即赋光标所在行的值至参照框，且光标定位到下一个参照框）</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>25</b></th>
  <td width="83"><font color="#404040" size="3" face="微软雅黑">↑</font></td>
  <td width="240"><font color="#282828" size="3" face="微软雅黑">表中向上移动光标</font></td>
  <td width="363"><font color="#282828" size="3" face="微软雅黑">同上</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>26</b></th>
  <td width="83"><font size="3" face="微软雅黑">空格</font></td>
  <td width="240"><font size="3" face="微软雅黑">选中/反向选</font></td>
  <td width="363"><font size="3" face="微软雅黑">复选框（搜索框右侧，如显示停用）</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="84"><b>27</b></th>
  <td width="83"><font size="3" face="微软雅黑">tab</font></td>
  <td width="240"><font size="3" face="微软雅黑">组件、区域顺序跳转</font></td>
  <td width="363"><font size="2" face="Microsoft YaHei">默认在表的第一条数据，跳转顺序：表的第一条数据（第二次循环时，跳至最后一次选择的那条数据）、组件（与确定、取消同行的复选框或其他按钮；已选、确定、取消不跳）、业务单元、搜索、搜索右侧的组件、循环&nbsp;<br>
  默认在表的</font><font size="3" face="®oÅÑ">第一条数据，跳转顺序：表的第一条数据（第二次循环时，跳至最后一次选择的那条数据）、搜索右侧的组件、组件（与确定、取消同行的复选框或其他按钮；已选、确定、取消不跳）、业务单元、搜索、循环</font></td>
  <td width="350" rowspan="6"><font size="3" face="微软雅黑">多选表参照面板</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>28</b></th>
  <td width="83"><font size="3" face="微软雅黑">shift+tab</font></td>
  <td width="240"><font size="3" face="微软雅黑">组件、区域反向顺序跳转</font></td>
  <td width="363">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>29</b></th>
  <td width="83"><font size="3" face="微软雅黑">↓</font></td>
  <td width="240"><font size="3" face="微软雅黑">表中向下移动光标</font></td>
  <td width="363"><font size="2" face="Microsoft YaHei">1.在数据区域内与表头移动&nbsp;<br>
  2.配合确定完成选择（整表编辑时：点击“确定”即赋光标所在行的值至参照框，且光标定位到下一个参照框）</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>30</b></th>
  <td width="83"><font color="#404040" size="3" face="微软雅黑">↑</font></td>
  <td width="240"><font color="#282828" size="3" face="微软雅黑">表中向上移动光标</font></td>
  <td width="363">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>31</b></th>
  <td width="83"><font size="3" face="微软雅黑">空格</font></td>
  <td width="240"><font size="3" face="微软雅黑">选中/反向选</font></td>
  <td width="363"><font size="2" face="Microsoft YaHei">选中行上/表头后，点击空格选中/反向选</font><font size="2" face="Microsoft YaHei">&nbsp;&nbsp;&nbsp;</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>32</b></th>
  <td width="83"><font size="3" face="微软雅黑">enter</font></td>
  <td width="240"><font size="3" face="微软雅黑">选择并确定</font></td>
  <td width="363"><font size="2" face="Microsoft YaHei">配合↑↓键使用，移动时，点击“enter”，&nbsp;<br>
  1.“勾选当前选项确定”并关闭弹窗&nbsp;<br>
  2.“勾选当前选项确定+之前已选的选项”并关闭弹窗</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>33</b></th>
  <td width="83"><font size="2" face="Microsoft YaHei">F4</font><font size="2" face="Microsoft YaHei">&nbsp;</font></td>
  <td width="240"><font color="#282828" size="3" face="微软雅黑">已选展开、已选收起</font></td>
  <td width="363">&nbsp;</td>
  <td width="350"><font size="3" face="微软雅黑">多选参照已选面板</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>34</b></th>
  <td width="83"><font size="3" face="微软雅黑">tab</font></td>
  <td width="240"><font color="#282828" size="3" face="微软雅黑">组件、区域顺序跳转</font></td>
  <td width="363"><font size="2" face="Microsoft YaHei">默认在树第一级第一个，跳转顺序：树第一级第一个（第二次循环时，选中的第一个）、组件（与确定、取消同行的复选框或其他按钮；确定、取消不跳）、业务单元、搜索、搜索右侧的组件、循环&nbsp;<br>
  默认在树第</font><font size="3" face="®oÅÑ">一级第一个，跳转顺序：树第一级第一个（第二次循环时，选中的第一个）、搜索右侧的组件、组件（与确定、取消同行的复选框或其他按钮；确定、取消不跳）、业务单元、搜索、循环</font></td>
  <td width="350" rowspan="12"><font size="3" face="微软雅黑">树单选参照面板</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>35</b></th>
  <td width="83"><font size="3" face="微软雅黑">shift+tab</font></td>
  <td width="240"><font size="3" face="微软雅黑">组件、区域反向顺序跳转</font></td>
  <td width="363"><font size="3" face="微软雅黑">同上，顺序相反</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>36</b></th>
  <td width="83"><font size="3" face="微软雅黑">↓</font></td>
  <td width="240"><font size="3" face="微软雅黑">树中向下移动光标</font></td>
  <td width="363"><font size="2" face="Microsoft YaHei">1.只在树内移动&nbsp;<br>
  2.配合确定完成选择（整表编辑时</font><font size="3" face="Microsoft YaHei">：点击“确定”即赋光标所在节点的值至参照框，且光标定位到下一个组件）</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>37</b></th>
  <td width="83">&nbsp;</td>
  <td width="240"><font color="#282828" size="3" face="微软雅黑">展开下拉按钮（如“更多”）</font></td>
  <td width="363">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>38</b></th>
  <td width="83">&nbsp;</td>
  <td width="240"><font color="#282828" size="3" face="微软雅黑">下拉按钮面板向下移动</font></td>
  <td width="363">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>39</b></th>
  <td width="83"><font size="3" face="微软雅黑">↑</font></td>
  <td width="240"><font size="3" face="微软雅黑">树中向上移动光标</font></td>
  <td width="363">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>40</b></th>
  <td width="83">&nbsp;</td>
  <td width="240"><font color="#282828" size="3" face="微软雅黑">下拉按钮面板向上移动</font></td>
  <td width="363">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>41</b></th>
  <td width="83"><font size="3" face="微软雅黑">→</font></td>
  <td width="240"><font color="#282828" size="3" face="微软雅黑">树展开</font></td>
  <td width="363">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="181"><b>42</b></th>
  <td width="83">&nbsp;</td>
  <td width="240"><font color="#282828" size="3" face="微软雅黑">展开下拉按钮的下一级</font></td>
  <td width="363"><font size="2" face="Microsoft YaHei">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<br>
  &nbsp;&nbsp;<br>
  &nbsp;&nbsp;&nbsp;<br>
  &nbsp;&nbsp;&nbsp;&nbsp;<br>
  &nbsp;<br>
  &nbsp;<br>
  下拉按钮面板中，焦点落在有下级的按钮上，点击→展开下一级，同时光标也存在下一级第一个按钮（这是再次点击上下键在下一级的按钮上下移动）&nbsp;<br>
  1.光标定位&nbsp; 2.点击→ 3.点击↓</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>43</b></th>
  <td width="83"><font color="#282828" size="3" face="微软雅黑">←</font></td>
  <td width="240"><font color="#282828" size="3" face="微软雅黑">树收起</font></td>
  <td width="363">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="189"><b>44</b></th>
  <td width="83">&nbsp;</td>
  <td width="240"><font size="3" face="微软雅黑">收起下拉按钮的下一级</font></td>
  <td width="363"><font size="2" face="Microsoft YaHei">&nbsp;&nbsp;&nbsp;&nbsp;<br>
  &nbsp;&nbsp;<br>
  &nbsp;&nbsp;&nbsp;<br>
  &nbsp;<br>
  下拉按钮面板中，焦点落在有上级的按钮上，点击←即可收起，恢复至上一级的样式&nbsp;<br>
  1.默认情况&nbsp; 2.点击←</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>45</b></th>
  <td width="83"><font size="3" face="微软雅黑">空格</font></td>
  <td width="240"><font size="3" face="微软雅黑">选中/反向选</font></td>
  <td width="363"><font size="2" face="Microsoft YaHei">复选框组件选中/反向选</font><font size="2" face="Microsoft YaHei">&nbsp;&nbsp;&nbsp;</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>46</b></th>
  <td width="83"><font size="3" face="微软雅黑">tab</font></td>
  <td width="240"><font color="#282828" size="3" face="微软雅黑">组件、区域顺序跳转</font></td>
  <td width="363"><font size="2" face="Microsoft YaHei">默认在树第一级第一个，跳转顺序：树第一级第一个（第二次循环时，选中的第一个）、组件（与确定、取消同行的复选框或其他按钮；已选、确定、取消不跳）、业务单元、搜索、搜索右侧的组件、循环&nbsp;<br>
  默认在树第</font><font size="3" face="®oÅÑ">一级第一个，跳转顺序：树第一级第一个（第二次循环时，选中的第一个）、搜索右侧的组件、组件（与确定、取消同行的复选框或其他按钮；已选、确定、取消不跳）、业务单元、搜索、循环</font></td>
  <td width="350" rowspan="13"><font size="3" face="微软雅黑">树多选参照面板</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>47</b></th>
  <td width="83"><font size="3" face="微软雅黑">shift+tab</font></td>
  <td width="240"><font size="3" face="微软雅黑">组件、区域反向顺序跳转</font></td>
  <td width="363"><font size="3" face="微软雅黑">同上，顺序相反</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>48</b></th>
  <td width="83"><font size="3" face="微软雅黑">↓</font></td>
  <td width="240"><font size="3" face="微软雅黑">树中向下移动光标</font></td>
  <td width="363"><font size="2" face="Microsoft YaHei">1.只在树内移动&nbsp;<br>
  2.配合确定完成选择（整表编辑时</font><font size="3" face="Microsoft YaHei">：点击“确定”即赋光标所在节点的值至参照框，且光标定位到下一个参照框）</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>49</b></th>
  <td width="83">&nbsp;</td>
  <td width="240"><font color="#282828" size="3" face="微软雅黑">展开下拉按钮（如“更多”）</font></td>
  <td width="363">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>50</b></th>
  <td width="83">&nbsp;</td>
  <td width="240"><font color="#282828" size="3" face="微软雅黑">下拉按钮面板向下移动</font></td>
  <td width="363">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>51</b></th>
  <td width="83"><font size="3" face="微软雅黑">↑</font></td>
  <td width="240"><font size="3" face="微软雅黑">树中向上移动光标</font></td>
  <td width="363">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>52</b></th>
  <td width="83">&nbsp;</td>
  <td width="240"><font color="#282828" size="3" face="微软雅黑">下拉按钮面板向上移动</font></td>
  <td width="363">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>53</b></th>
  <td width="83"><font size="3" face="微软雅黑">→</font></td>
  <td width="240"><font color="#282828" size="3" face="微软雅黑">树展开</font></td>
  <td width="363">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="182"><b>54</b></th>
  <td width="83">&nbsp;</td>
  <td width="240"><font color="#282828" size="3" face="微软雅黑">展开下拉按钮的下一级</font></td>
  <td width="363"><font size="2" face="Microsoft YaHei">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<br>
  &nbsp;&nbsp;<br>
  &nbsp;&nbsp;&nbsp;<br>
  &nbsp;&nbsp;&nbsp;&nbsp;<br>
  &nbsp;<br>
  &nbsp;<br>
  下拉按钮面板中，焦点落在有下级的按钮上，点击→展开下一级，同时光标也存在下一级第一个按钮（这是再次点击上下键在下一级的按钮上下移动）&nbsp;<br>
  1.光标定位&nbsp; 2.点击→ 3.点击↓</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>55</b></th>
  <td width="83"><font color="#282828" size="3" face="微软雅黑">←</font></td>
  <td width="240"><font color="#282828" size="3" face="微软雅黑">树收起</font></td>
  <td width="363">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="196"><b>56</b></th>
  <td width="83">&nbsp;</td>
  <td width="240"><font size="3" face="微软雅黑">收起下拉按钮的下一级</font></td>
  <td width="363"><font size="2" face="Microsoft YaHei">&nbsp;&nbsp;&nbsp;&nbsp;<br>
  &nbsp;&nbsp;<br>
  &nbsp;&nbsp;&nbsp;<br>
  &nbsp;<br>
  下拉按钮面板中，焦点落在有上级的按钮上，点击←即可收起，恢复至上一级的样式&nbsp;<br>
  1.默认情况&nbsp; 2.点击←</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="28"><b>57</b></th>
  <td width="83"><font size="3" face="微软雅黑">空格</font></td>
  <td width="240"><font size="3" face="微软雅黑">选中/反向选</font></td>
  <td width="363"><font size="2" face="Microsoft YaHei">1.选可选的节点/根节点，点击空格选中/反向选</font><font size="2" face="Microsoft YaHei">&nbsp;&nbsp;&nbsp;<br>
  </font><font size="2" face="Microsoft YaHei">2.复选框组件选中/反向选</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="46"><b>58</b></th>
  <td width="83"><font size="3" face="微软雅黑">enter</font></td>
  <td width="240"><font size="3" face="微软雅黑">选择并确定</font></td>
  <td width="363"><font size="2" face="Microsoft YaHei">配合↑↓键使用，移动时，点击“enter”，&nbsp;<br>
  1.“勾选当前选项确定”并关闭弹窗&nbsp;<br>
  2.“勾选当前选项确定+之前已选的选项”并关闭弹窗</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="300"><b>59</b></th>
  <td width="83"><font size="3" face="微软雅黑">tab</font></td>
  <td width="240"><font color="#282828" size="3" face="微软雅黑">组件、区域顺序跳转</font></td>
  <td width="363"><font size="2" face="Microsoft YaHei">常用页签优先，常用中无数据显示全部数据&nbsp;<br>
  常用：默认在表的第一条数据且选中，顺序：表的第一条数据（第二次循环时，选中的第一条数据）、组件（与确定、取消同行的复选框或其他按钮；确定、取消不跳）、业务单元、搜索、组件（搜索右侧的组件；列设置、清空不跳）、循环&nbsp;<br>
  全部数据：默认在树第一级第一个，跳转顺序：树第一级第一个（第二次循环时，选中的第一个）、表搜索、组件（搜索右侧的组件；列设置、设为常用不跳）、表（循环时，若切换树节点表跳第一条数据，若树无切换时表跳退后一次选择的数据）、组件（与确定、取消同行的复选框或其他按钮；确定、取消不跳）、业务单元、页签、树搜索、循环&nbsp;<br>
  常用：默认在表的第一条数据且选中，顺序</font><font size="3" face="Microsoft YaHei">：表的第一条数据（第二次循环时，选中的第一条数据）、组件（搜索右侧的组件；列设置、清空不跳）、组件（与确定、取消同行的复选框或其他按钮；确定、取消不跳）、业务单元、搜索、循环&nbsp;<br>
  全部数据：默认在树第一级第一个，跳转顺序：树第一级第一个（第二次循环时，选中的第一个）、表搜索、表（循环时，若切换树节点表跳第一条数据，若树无切换时表跳退后一次选择的数据）、组件（搜索右侧的组件；列设置、设为常用不跳）、组件（与确定、取消同行的复选框或其他按钮；确定、取消不跳）、业务单元、页签、树搜索、循环</font></td>
  <td width="350" rowspan="16"><font size="3" face="微软雅黑">树表单选参照面板</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>60</b></th>
  <td width="83"><font size="3" face="微软雅黑">shift+tab</font></td>
  <td width="240"><font size="3" face="微软雅黑">组件、区域反向顺序跳转</font></td>
  <td width="363"><font size="3" face="微软雅黑">同上，顺序相反</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>61</b></th>
  <td width="83"><font size="3" face="微软雅黑">↓</font></td>
  <td width="240"><font size="3" face="微软雅黑">树中向下移动光标，并选择</font></td>
  <td width="363"><font size="2" face="Microsoft YaHei">只在树内移动&nbsp;<br>
  &nbsp;<br>
  </font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="43"><b>
  62</b></th>
  <td width="83">&nbsp;</td>
  <td width="240"><font size="3" face="微软雅黑">表中向下移动光标</font></td>
  <td width="363"><font size="2" face="Microsoft YaHei">1.只在表内移动&nbsp;<br>
  2.配合确定完成选择（整表编辑时</font><font size="3" face="Microsoft YaHei">：点击“确定”即赋光标所在行的值至参照框，且光标定位到下一个参照框）</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>63</b></th>
  <td width="83">&nbsp;</td>
  <td width="240"><font color="#282828" size="3" face="微软雅黑">展开下拉按钮（如“更多”）</font></td>
  <td width="363">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>64</b></th>
  <td width="83">&nbsp;</td>
  <td width="240"><font color="#282828" size="3" face="微软雅黑">下拉按钮面板向下移动</font></td>
  <td width="363">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>65</b></th>
  <td width="83"><font size="3" face="微软雅黑">↑</font></td>
  <td width="240"><font size="3" face="微软雅黑">树中向上移动光标，并选择</font></td>
  <td width="363"><font size="3" face="微软雅黑">同上</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>66</b></th>
  <td width="83">&nbsp;</td>
  <td width="240"><font size="3" face="微软雅黑">表中向上移动光标</font></td>
  <td width="363"><font size="3" face="微软雅黑">同上</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>67</b></th>
  <td width="83">&nbsp;</td>
  <td width="240"><font color="#282828" size="3" face="微软雅黑">下拉按钮面板向上移动</font></td>
  <td width="363">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>68</b></th>
  <td width="83"><font size="3" face="微软雅黑">→</font></td>
  <td width="240"><font size="3" face="微软雅黑">树展开</font></td>
  <td width="363">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="182"><b>69</b></th>
  <td width="83">&nbsp;</td>
  <td width="240"><font size="3" face="微软雅黑">展开下拉按钮的下一级</font></td>
  <td width="363"><font size="2" face="Microsoft YaHei">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<br>
  &nbsp;&nbsp;<br>
  &nbsp;&nbsp;&nbsp;<br>
  &nbsp;&nbsp;&nbsp;&nbsp;<br>
  &nbsp;<br>
  &nbsp;<br>
  下拉按钮面板中，焦点落在有下级的按钮上，点击→展开下一级，同时光标也存在下一级第一个按钮（这是再次点击上下键在下一级的按钮上下移动）&nbsp;<br>
  1.光标定位&nbsp; 2.点击→ 3.点击↓</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="30"><b>70</b></th>
  <td width="83"><font color="#282828" size="3" face="微软雅黑">shift+→</font></td>
  <td width="240"><font color="#282828" size="3" face="微软雅黑">页签向右切换</font></td>
  <td width="363"><font color="#282828" size="3" face="微软雅黑">用快捷键直接向右切换，焦点定位默认或上一次选中的组件/树/表（若常用中无内容，定位搜索）</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>71</b></th>
  <td width="83"><font size="3" face="微软雅黑">←</font></td>
  <td width="240"><font color="#282828" size="3" face="微软雅黑">树收起</font></td>
  <td width="363"><font color="#282828" size="3" face="微软雅黑">树型结构</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="194"><b>72</b></th>
  <td width="83">&nbsp;</td>
  <td width="240"><font size="3" face="微软雅黑">收起下拉按钮的下一级</font></td>
  <td width="363"><font size="2" face="Microsoft YaHei">&nbsp;&nbsp;&nbsp;&nbsp;<br>
  &nbsp;&nbsp;<br>
  &nbsp;&nbsp;&nbsp;<br>
  &nbsp;<br>
  下拉按钮面板中，焦点落在有上级的按钮上，点击←即可收起，恢复至上一级的样式&nbsp;<br>
  1.默认情况&nbsp; 2.点击←</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="28"><b>73</b></th>
  <td width="83"><font color="#282828" size="3" face="微软雅黑">shift+←</font></td>
  <td width="240"><font color="#282828" size="3" face="微软雅黑">页签向左切换</font></td>
  <td width="363"><font color="#282828" size="3" face="微软雅黑">用快捷键直接向左切换，焦点定位默认或上一次选中的组件/树/表（若常用中无内容，定位搜索）</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>74</b></th>
  <td width="83"><font size="3" face="微软雅黑">空格</font></td>
  <td width="240"><font size="3" face="微软雅黑">选中/反向选</font></td>
  <td width="363"><font size="3" face="微软雅黑">复选框组件选中/反向选</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>75</b></th>
  <td width="83"><font size="3" face="微软雅黑">tab</font></td>
  <td width="240"><font color="#282828" size="3" face="微软雅黑">组件、区域顺序跳转</font></td>
  <td width="363"><font size="2" face="Microsoft YaHei">常用页签优先，常用中无数据显示全部数据&nbsp;<br>
  常用：默认在表的第一条数据且选中，顺序：表的第一条数据（第二次循环时，选中的第一个）、组件（与确定、取消同行的复选框或其他按钮；确定、取消不跳）、业务单元、搜索、组件（搜索右侧的组件；列设置、清空常用不跳）、循环&nbsp;<br>
  全部数据：默认在树第一级第一个，跳转顺序：树第一级第一个（第二次循环时，选中的第一个）、表搜索、组件（搜索右侧的组件；列设置、设为常用不跳）、表（循环时，若切换树节点表跳第一条数据，若树无切换时表跳退后一次选择的数据）、组件（与确定、取消同行的复选框或其他按钮；已选、确定、取消不跳）、业务单元、页签、树搜索、循环&nbsp;<br>
  常用：默认在表的第一条数据且选中，顺序</font><font size="3" face="®oÅÑ">：表的第一条数据（第二次循环时，选中的第一个）、组件（搜索右侧的组件；列设置、清空常用不跳）、组件（与确定、取消同行的复选框或其他按钮；确定、取消不跳）、业务单元、搜索、循环&nbsp;<br>
  全部数据：默认在树第一级第一个，跳转顺序：树第一级第一个（第二次循环时，选中的第一个）、表搜索、表（循环时，若切换树节点表跳第一条数据，若树无切换时表跳退后一次选择的数据）、组件（搜索右侧的组件；列设置、设为常用不跳）、组件（与确定、取消同行的复选框或其他按钮；已选、确定、取消不跳）、业务单元、页签、树搜索、循环</font></td>
  <td width="350" rowspan="17"><font size="3" face="微软雅黑">树表多选参照</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>76</b></th>
  <td width="83"><font size="3" face="微软雅黑">shift+tab</font></td>
  <td width="240"><font size="3" face="微软雅黑">组件、区域反向顺序跳转</font></td>
  <td width="363"><font size="3" face="微软雅黑">同上，顺序相反</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>77</b></th>
  <td width="83"><font size="3" face="微软雅黑">↓</font></td>
  <td width="240"><font size="3" face="微软雅黑">树中向下移动光标，并选择</font></td>
  <td width="363"><font size="3" face="微软雅黑">只在树内移动</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>78</b></th>
  <td width="83">&nbsp;</td>
  <td width="240"><font size="3" face="微软雅黑">表中向下移动光标</font></td>
  <td width="363"><font size="2" face="Microsoft YaHei">1.只在表内移动（包含表头）&nbsp;<br>
  2.配合确定完成选择（整表编辑时：点击“确定”即赋光标所在行的值至参照框，且光标定位到下一个参照框）</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>79</b></th>
  <td width="83">&nbsp;</td>
  <td width="240"><font color="#282828" size="3" face="微软雅黑">展开下拉按钮（如“更多”）</font></td>
  <td width="363">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>80</b></th>
  <td width="83">&nbsp;</td>
  <td width="240"><font color="#282828" size="3" face="微软雅黑">下拉按钮面板向下移动</font></td>
  <td width="363">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>81</b></th>
  <td width="83"><font size="3" face="微软雅黑">↑</font></td>
  <td width="240"><font size="3" face="微软雅黑">树中向上移动光标，并选择</font></td>
  <td width="363"><font size="3" face="微软雅黑">同上</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>82</b></th>
  <td width="83">&nbsp;</td>
  <td width="240"><font size="3" face="微软雅黑">表中向上移动光标</font></td>
  <td width="363"><font size="3" face="微软雅黑">同上</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>83</b></th>
  <td width="83">&nbsp;</td>
  <td width="240"><font color="#282828" size="3" face="微软雅黑">下拉按钮面板向上移动</font></td>
  <td width="363">&nbsp;</td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>84</b></th>
  <td width="83"><font size="3" face="微软雅黑">→</font></td>
  <td width="240"><font color="#282828" size="3" face="微软雅黑">树展开</font></td>
  <td width="363"><font size="3" face="微软雅黑">1.点击“→”展开下级节点，此时点击“→”或“↓”都可以跳至下一级上</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="180"><b>85</b></th>
  <td width="83">&nbsp;</td>
  <td width="240"><font color="#282828" size="3" face="微软雅黑">展开下拉按钮的下一级</font></td>
  <td width="363"><font size="2" face="Microsoft YaHei">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<br>
  &nbsp;&nbsp;<br>
  &nbsp;&nbsp;&nbsp;<br>
  &nbsp;&nbsp;&nbsp;&nbsp;<br>
  &nbsp;<br>
  &nbsp;<br>
  下拉按钮面板中，焦点落在有下级的按钮上，点击→展开下一级，同时光标也存在下一级第一个按钮（这是再次点击上下键在下一级的按钮上下移动）&nbsp;<br>
  1.光标定位&nbsp; 2.点击→ 3.点击↓</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="30"><b>86</b></th>
  <td width="83"><font color="#282828" size="3" face="微软雅黑">shift+→</font></td>
  <td width="240"><font color="#282828" size="3" face="微软雅黑">页签向左切换</font></td>
  <td width="363"><font color="#282828" size="3" face="微软雅黑">用快捷键直接向左切换，焦点定位默认或上一次选中的组件/树/表（若常用中无内容，定位搜索）</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>87</b></th>
  <td width="83"><font color="#282828" size="3" face="微软雅黑">←</font></td>
  <td width="240"><font color="#282828" size="3" face="微软雅黑">树收起</font></td>
  <td width="363"><font color="#282828" size="3" face="微软雅黑">树型结构</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="190"><b>88</b></th>
  <td width="83">&nbsp;</td>
  <td width="240"><font size="3" face="微软雅黑">收起下拉按钮的下一级</font></td>
  <td width="363"><font size="2" face="Microsoft YaHei">&nbsp;&nbsp;&nbsp;&nbsp;<br>
  &nbsp;&nbsp;<br>
  &nbsp;&nbsp;&nbsp;<br>
  &nbsp;<br>
  下拉按钮面板中，焦点落在有上级的按钮上，点击←即可收起，恢复至上一级的样式&nbsp;<br>
  1.默认情况&nbsp; 2.点击←</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="29"><b>89</b></th>
  <td width="83"><font color="#282828" size="3" face="微软雅黑">shift+←</font></td>
  <td width="240"><font color="#282828" size="3" face="微软雅黑">页签向左切换</font></td>
  <td width="363"><font color="#282828" size="3" face="微软雅黑">用快捷键直接向左切换，焦点定位默认或上一次选中的组件/树/表（若常用中无内容，定位搜索）</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>90</b></th>
  <td width="83"><font size="3" face="微软雅黑">空格</font></td>
  <td width="240"><font size="3" face="微软雅黑">选中/反向选</font></td>
  <td width="363"><font size="2" face="Microsoft YaHei">1.选可选的节点/根节点，点击空格选中/反向选</font><font size="2" face="Microsoft YaHei">&nbsp;&nbsp;&nbsp;<br>
  </font><font size="2" face="Microsoft YaHei">2.复选框组件选中/反向选</font></td></tr>
<tr><th align="center" valign="bottom" bgcolor="#B0B0B0" width="24" height="15"><b>91</b></th>
  <td width="83"><font size="3" face="微软雅黑">enter</font></td>
  <td width="240"><font size="3" face="微软雅黑">选择并确定</font></td>
  <td width="363"><font size="2" face="Microsoft YaHei">配合↑↓键使用，移动时，点击“enter”，&nbsp;<br>
  1.“勾选当前选项确定”并关闭弹窗&nbsp;<br>
  2.“勾选当前选项确定+之前已选的选项”并关闭弹窗</font></td></tr>
</tbody></table>


