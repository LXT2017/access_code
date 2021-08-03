<template>
<div>
  <!-- 个人信息 -->
  <!-- 顶部蓝色背景 -->
  <div class="topBack">智慧浙理校园通行码</div>
 <div class="topinfo">
      <span>职工号</span>
      <span class="topinfospan">xxxxxx</span>
      <span class="topinfospan">姓名</span>
      <span class="topinfospan">xx</span>
</div>
<div class="topinfo">
      <span>学院部</span>
      <span class="topinfospan">体育教研部  (军训工作部)</span>
</div>
<div >
      <div class="date">{{dateFormat(newDate)}}</div>
      <div class="time">{{timeFormat(newDate)}}</div>
    </div>

<div class="topinfo"> 
  <span style="padding-left: 5%">有效期限</span>
  <span class="topinfospan">2021-07-03  —  2021-09-05</span>
</div>

<!-- 中间的二维码 -->

    <div class="imageinfo">
      <img class="image" src="../assets/qr2.jpg" alt="qr">
    </div>

  <!-- 底部信息 -->
    <div class="bottleinfo">
    <div>二维码定期更新，请勿截图</div>
    <div>温馨提醒：提前打开 快速通行</div>
    <div>信息化办公室 Copyright@2021</div>
  </div>
</div>
</template>

<script>
export default {
      data() {
        return {
          // 当前时间
          newDate: new Date()
        }
      },
      mounted() {
        //使用定时器每秒向div写入当前时间
        let that = this
        this.timer = setInterval(function () {
          that.newDate = new Date().toLocaleString()
        })
      },

      // 分别是日期和时间
      methods: {
      dateFormat () {
          var date = new Date()
          var month = date.getMonth() + 1 < 10 ? '0' + (date.getMonth() + 1) : date.getMonth() + 1
          var day = date.getDate() < 10 ? '0' + date.getDate() : date.getDate()
          return month + '月' + day + '日 '
        },
        timeFormat () {
          var date = new Date()
          var hours = date.getHours() < 10 ? '0' + date.getHours() : date.getHours()
          var minutes = date.getMinutes() < 10 ? '0' + date.getMinutes() : date.getMinutes()
          var seconds = date.getSeconds() < 10 ? '0' + date.getSeconds() : date.getSeconds()
          return hours + ':' + minutes + ':' + seconds
        }

             // 时间格式化
      // dateFormat () {
      //     var date = new Date()
      //     // var year = date.getFullYear()
      //     var month = date.getMonth() + 1 < 10 ? '0' + (date.getMonth() + 1) : date.getMonth() + 1
      //     var day = date.getDate() < 10 ? '0' + date.getDate() : date.getDate()
      //     var hours = date.getHours() < 10 ? '0' + date.getHours() : date.getHours()
      //     var minutes = date.getMinutes() < 10 ? '0' + date.getMinutes() : date.getMinutes()
      //     var seconds = date.getSeconds() < 10 ? '0' + date.getSeconds() : date.getSeconds()
      //     // let week = date.getDay() 
      //     // let weekArr = [ '星期日', '星期一', '星期二', '星期三', '星期四', '星期五', '星期六' ]
      //     // 拼接 时间格式处理
      //     return month + '月' + day + '日 ' + '\n' + hours + ':' + minutes + ':' + seconds
      //   }
      }
}
</script>

<style scoped>
body {
  padding: 0;
  margin: 0;
}
.topBack{
  position: relative;
  height: 45px;
  background-color: #3777B5;
  color: #F8F3EB;
  margin: 8px;
  font-size: 22px;
  font-weight: bold;
  text-align: center;
  line-height: 45px;
}

.topinfo{
  font-size: 17px;
  font-weight: 400;
  padding: 2px 11px;
}
.topinfospan{
  font-size: 18px;
  font-weight:540;
  margin-left: 25px;
}
.date{
  position: relative;
  font-size: 28px;
  font-weight: 550;
  text-align: center;
  margin-top: 10px;
}
.time{
  position: relative;
  font-size: 44px;
  font-weight: 550;
  text-align: center;
  margin-top: 5px;
}
.imageinfo{
  position: relative;
  /* margin: 10px 14px; */
  text-align: center;
  margin: 7% 7% 5% 7%;
}
.image{
  position: relative;
  height: 76%;
  width: 76%;
}

.bottleinfo{
  margin: 4px;
  text-align: center;
  line-height: 200%;
  font-size: 18px;
}
</style>
