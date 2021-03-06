# Echart基础入门

## 一、基础柱状图

```
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <!-- 引入echarts包 -->
    <script src="echarts.js"></script>
    <title>Document</title>
</head>

<body>
    <!-- 为 ECharts 准备一个定义了宽高的 DOM -->
    <div id="firstchart" style="width: 600px;height: 400px; display:inline-block;"></div>

    <script>
        var firstChart = echarts.init(document.getElementById('firstchart'));

        var option = {

            xAxis: {
                type: 'category',
            },
            yAxis: {},
            series: [{
                type: 'bar',
                data: [4, 3, 6, 1],
            }]
        }

        firstChart.setOption(option);
    </script>

</body>

</html>

```

## 二、两个div并列摆放

```
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <!-- 引入echarts包 -->
    <script src="echarts.js"></script>
    <title>Document</title>
</head>

<body>
    <!-- 为 ECharts 准备一个定义了宽高的 DOM -->
    <div id="firstchart" style="width: 600px;height: 400px; display:inline-block;"></div>
    <div id="secondchart" style="width: 600px;height: 400px;display:inline-block;"></div>
    <!--如果想横向摆放 display:inline-block; -->

    <script>
        var firstChart = echarts.init(document.getElementById('firstchart'));

        var option = {

            xAxis: {
                type: 'category',
            },
            yAxis: {},
            series: [{
                type: 'bar',
                data: [4, 3, 6, 1],
            }]
        }

        firstChart.setOption(option);
        var secondChart = echarts.init(document.getElementById('secondchart'));
        var option = {

            xAxis: {
                type: 'category',
            },
            yAxis: {},
            series: [{
                type: 'bar',
                data: [4, 3, 6, 1],
            }]
        }
        secondChart.setOption(option);

    </script>

</body>

</html>

```

## 三、使用jQuery包导入数据

```
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <!-- 引入echarts包 -->
    <script src="echarts.js"></script>
    <!-- 引入jquery包 -->
    <script src="jquery-3.6.0.js"></script>
    <title>Document</title>
</head>

<body>
    <!-- 为 ECharts 准备一个定义了宽高的 DOM -->
    <div id="firstchart" style="width: 600px;height: 400px; display:inline-block;"></div>
    <div id="secondchart" style="width: 600px;height: 400px;display:inline-block;"></div>
    <!--如果想横向摆放 display:inline-block; -->

    <script>
        $.get('work.csv', function (data) {
        
           <!-- 处理data中的字符 -->
            data = data.split('\r\n');
            var newdata = [];
            var company = [];
            var valued = [];
            console.log(data)
            for (var i = 1; i < data.length; i++) {
                var temp = data[i].split(',');
                newdata.push(temp);
                company.push(temp[0]);
                valued.push(temp[2]);
            }
            var firstChart = echarts.init(document.getElementById('firstchart'));

            var option = {

                xAxis: {
                    type: 'category',
                    data: company,
                },
                yAxis: {},
                series: [{
                    type: 'bar',
                    data: valued,
                }]
            }

            firstChart.setOption(option);

        })
        /*          */
        var secondChart = echarts.init(document.getElementById('secondchart'));
        var option = {

            xAxis: {
                type: 'category',
            },
            yAxis: {},
            series: [{
                type: 'bar',
                data: [4, 3, 6, 1],
            }]
        }
        secondChart.setOption(option);

    </script>

</body>

</html>


```

## 资源：

官方文档：https://echarts.apache.org/handbook/zh/get-started/

Echarts官方网站： https://echarts.apache.org/zh/index.html

资源网站：https://www.makeapie.cn/echarts

Web网页的基础知识：http://www.w3school.com.cn/

