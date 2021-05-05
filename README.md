# mFilterToolbar

mFilterToolbar 是一款mui风格的移动端h5气泡级联框，支持可选择任意层级、默认值、分隔符




首先引入mui和jq库，mFilterToolbar.css（mFilterToolbar的样式）
```html
 <script src="https://cdn.bootcdn.net/ajax/libs/jquery/3.6.0/jquery.min.js"></script>
    <script src="https://cdn.bootcdn.net/ajax/libs/mui/3.7.1/js/mui.min.js"></script>
    <link
      href="https://cdn.bootcdn.net/ajax/libs/mui/3.7.1/css/mui.min.css"
      rel="stylesheet"
    />
    <link href="css/mFilterToolbar.css" rel="stylesheet" />
     <script src="js/mFilterToolbar.js"></script>
```
## 使用方法：
直接调用mFilterToolbar方法，并传入配置项：

   ```javascript
       // 实例化一个ft对象
    var ft = new mFilterToolbar({
      defaultValue: {
        tabValue: "1",
        cacheSortObj: {
          sortName: "sortType2",
          sortType: "desc",
        },
      }, //默认值对象
      onTabClick: function (obj) {
        //tab点击完成后的回调函数
        console.log(obj);
        //在这里可以调用加载列表代码...
      },
    });
   ```

#### input：


对应文本框的选择器，字符串类型


#### data：


mCascader的数据。Array类型，树结构，data中的节点必须要有以下属性：

```javascript
 data = [{
   id:'',  // 必须,唯一的id值，String类型
   name:'', //必须,对应mCascader节点的显示文本 ，String类型
   children:[...] //子节点 ，Array类型
    },...]
```

#### 获取mCascader当前的id值(2种)：


1.mCascader.currtId

2.$('#demo').data('id')或$(mCascader.options.input).data('id')


#### 返回上一层级：


mCascader.back()
      
      
#### 清空mCascader数据及重置界面：


mCascader.clear()
     

## 例子：
##### mcascader的DOM不写死到js中，保留了原本组件的结构，方便你自定义组件的样式
``` html
 
    <div class="filterbox">
      <div class="filter-tab">
        <div class="tab-l active" data-to="tab-l">
          <span> <span class="mui-icon iconfont icon-guolvqi"></span>筛选</span>
        </div>
        <div class="tab-r" data-to="tab-r">
          <span> <span class="mui-icon iconfont icon-paixu"></span>排序</span>
        </div>
      </div>
      <div class="tab-content">
        <div class="l-cont" id="tab-l">
          <div class="tc-btn active" data-value="0">
            全部<span class="mui-badge mui-badge-danger allCount">0</span>
          </div>
          <div class="tc-btn" data-value="1">
            <!-- 设置tab对应的值-->
            tab1<span class="mui-badge mui-badge-danger countNum1">0</span>
          </div>
          <div class="tc-btn" data-value="2">
            tab2<span class="mui-badge mui-badge-danger countNum2">0</span>
          </div>
          <div class="tc-btn" data-value="3">
            tab3<span class="mui-badge mui-badge-danger countNum3">0</span>
          </div>
        </div>
        <div class="r-cont" id="tab-r" style="display: none">
          <div class="tc-btn active" data-value="sortType1">
            <!--排序对应的key 升序为asc  降序为desc 。  默认为asc 。点击后会toggle这两个值-->
            按热度<span class="mui-icon iconfont icon-paixu1"></span>
          </div>
          <div class="tc-btn" data-value="sortType2">
            按时间<span class="mui-icon iconfont icon-paixu1"></span>
          </div>
          <div class="tc-btn" data-value="sortType3">
            按评分<span class="mui-icon iconfont icon-paixu1"></span>
          </div>
        </div>
      </div>
    </div>
    <list>列表...</list>

  <script src="js/mFilterToolbar.js"></script>
  <script>
    // 实例化一个ft对象
    var ft = new mFilterToolbar({
      defaultValue: {
        tabValue: "1",
        cacheSortObj: {
          sortName: "sortType2",
          sortType: "desc",
        },
      }, //默认值对象
      onTabClick: function (obj) {
        //tab点击完成后的回调函数
        console.log(obj);
        //在这里可以调用加载列表代码...
      },
    });
  </script>
```


欢迎你参与贡献！👏
