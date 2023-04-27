# vue前端词云图实现

## 使用到的技术
- Vue3、Vite、jqcloud2、jquery、randomcolor
- 生成词云图方法
- 1、通过jquery、jqcloud2来进行词云图生成
- 2、通过randomcolor来随机颜色
## onMounted
- onMounted钩子是vue3新添加的特性，组合式api，setup中调用。
## 全部代码
### vue3代码
```vue
<template>
  <div id="word-cloud"></div>
</template>

<script setup lang="ts">
import { ref, onMounted } from "vue";
import $ from "jquery";
import "jqcloud2";
import RandomColor from "randomcolor";
onMounted(() => {
  // test 数据
  const wordcloudData = [
    { text: "好吃", weight: 50 },
    { text: "美味极了", weight: 32 },
    { text: "还可以把", weight: 1 },
    { text: "不太行", weight: 6 },
    { text: "一般", weight: 20 }
  ];
  // 随机颜色
  const data = wordcloudData.map((word, index) => {
    return { text: word.text, weight: word.weight, color: RandomColor() };
  });

  // 使用jqcloud库生成词云图
  $("#word-cloud").jQCloud(data, {
    // 画布大小
    width: 500,
    height: 300,
    // 自动大小设置
    shape: "rectangular",
    autoResize: true,
    // 大小的随机阈值
    fontSize: {
      from: 0.1,
      to: 0.02
  }
  });
});
</script>
<!-- 以下可有可无 -->
<style scoped>
#word-cloud {
  width: 200px;
  height: 100px;
  margin: 0 auto;
}
</style>
```
### HTML代码
```HTML
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>词云图</title>
  <script src="https://cdn.bootcdn.net/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
  <script src="https://cdn.bootcdn.net/ajax/libs/jqcloud/1.0.4/jqcloud-1.0.4.min.js"></script>
  <link rel="stylesheet" href="https://cdn.bootcdn.net/ajax/libs/jqcloud/1.0.4/jqcloud.min.css" />
  <style>
    #word-cloud {
      width: 600px;
      height: 400px;
      margin: 0 auto;
    }
  </style>
</head>
<body>
  <div id="word-cloud"></div>
  <script>
    $(function() {
      var data = [
    	{ text: "好吃", weight: 50 },
    	{ text: "美味极了", weight: 32 },
    	{ text: "还可以把", weight: 1 },
    	{ text: "不太行", weight: 6 },
    	{ text: "一般", weight: 20 }
      ];
      
      // 使用jqcloud库生成词云图
      $("#word-cloud").jQCloud(data, {
        width: 600,
        height: 400
      });
    });
  </script>
</body>
</html>
```
## 简介
- 权重最大的关键词会一直保持在中间
- 效果图
{{< figure src="/images/worldcloud.png" title="词云图">}}

## 为了方便起见，做了打开即用的词云图生成工具，代码如下
```HTML
<!DOCTYPE html>
<html>

<head>
  <meta charset="UTF-8">
  <title>词云图</title>
  <script src="https://cdn.bootcdn.net/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
  <script src="https://cdn.bootcdn.net/ajax/libs/jqcloud/1.0.4/jqcloud-1.0.4.min.js"></script>
  <link rel="stylesheet" href="https://cdn.bootcdn.net/ajax/libs/jqcloud/1.0.4/jqcloud.min.css" />
  <style>
    #word-cloud {
      width: 600px;
      height: 400px;
      margin: 0 auto;
      background-color: #100F22;
    }
  </style>
</head>

<body>
  <h1>临时词云图生成工具：传入text和weight</h1>
  <div id="word-cloud"></div>
  <div>
    <button id="clear-btn">清空数据</button>
  </div>
  <div>
    <label for="text-input">输入数据（格式为JSON数组）:[
      { "text": "好吃", "weight": 50 },
      { "text": "美味极了", "weight": 32 },
      { "text": "还可以把", "weight": 1 },
      { "text": "不太行", "weight": 6 },
      { "text": "一般", "weight": 20 }
      ]
    </label>
    <textarea name="text-input" id="text-input" cols="50" rows="10"></textarea>
    <button id="submit-btn">生成词云图</button>
  </div>

  <script>
    $(function () {
      var cloudData;
      var cloudInstance;

      function updateCloud(newData) {
        if (cloudInstance) {
          cloudInstance.jQCloud('destroy');
          cloudInstance = null;
        }
        $("#word-cloud").empty()
        cloudInstance = $("#word-cloud").jQCloud(newData, {
          width: 600,
          height: 400
        });
        $("#remove-btn").prop('disabled', false);
      }

      function clearData() {
        if (cloudInstance) {
          cloudInstance.jQCloud('destroy');
          cloudInstance = null;
        }
        cloudData = [];
        $("#text-input").val("");
      }

      function loadData(jsonText) {
        try {
          var formattedJsonText = JSON.stringify(JSON.parse(jsonText), null, 2);
          $("#text-input").val(formattedJsonText);
          var newData = JSON.parse(jsonText);
          if (Array.isArray(newData)) {
            cloudData = newData;
            updateCloud(cloudData);
          } else {
            alert("输入数据格式错误，请输入一个JSON数组");
          }
        } catch (e) {
          alert("输入数据格式错误，请输入一个JSON数组");
        }
      }

      $("#clear-btn").click(function () {
        clearData();
      });

      $("#submit-btn").click(function () {
        var jsonText = $("#text-input").val();
        loadData(jsonText);
      });
    });

  </script>
</body>

</html>
```
## 结语
- Vue3生成词云图实现

