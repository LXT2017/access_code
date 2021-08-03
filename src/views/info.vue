<template>
<div>
  <!-- 顶部蓝色背景 -->
  <div v-if="id=='0'" class="topBackUnderGraduate"></div>
  <div v-else class="topBackGraduate"></div>

<!-- 中间的二维码 -->
  <div class="card">
    <div class="date">
      <div>{{dateFormat(newDate)}}</div>
      <div>{{timeFormat(newDate)}}</div>
    </div>
    <div class="topinfo">
      <span>{{college}}</span>
      <span class="xuehao">{{number}}</span>
    </div>
    <div class="imageinfo">
      <img v-if="id=='0'" class="image" src="../assets/qr.jpg" alt="qr">
      <img v-else class="image" src="../assets/qr1.jpg" alt="qr">
    </div>
    <div class="middleinfo">
      <span class="middleinfo1" >{{name}}</span>
      <span class="middleinfo1" style="color: blue">刷新</span>
    </div>
  </div>

  <!-- 底部信息 -->
    <div class="bottleinfo">
    <div>2021-07-05 至 2021-09-30</div>
    <div>
      <span class="bottletext">通行码类型： </span>
      <span>普通通行码</span>
    </div>

    <div>
      <span class="bottletext">剩余次数： </span>
      <span>200</span>
    </div>
  

    <!-- <div>
      <span class="bottletext">第一次刷码时间： </span>
      <span>2021-03-21 20:49:33</span>
    </div> -->
  </div>

  <div class="lastinfo">
    <span class="lasttext">通行记录</span>
  </div>
</div>
</template>

<script>
export default {
      data() {
        return {
          // 当前时间
          newDate: new Date(),
          name: '',
          college:'',
          number:'',
          id:''
        }
      },
      created(){
        var college = localStorage.getItem("college")
        var number = localStorage.getItem("number")
        var name = localStorage.getItem("name")
        var id = localStorage.getItem("id")
        if(college!=null||number!=null||name!=null||id!=null){
          this.college=college
          this.number=number
          this.name=name
          this.id=id
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
.topBackUnderGraduate{
  height: 200px;
  background-color: #3B70E4;
}
.topBackGraduate{
  height: 200px;
  background-color: #FF5505;
}
.card{
  margin: 0 6%;
  position: relative;
  opacity: 0.99;
  background-color: #FFFFFF;
  /* height: 510px; */
  width: 88%;
  border-radius: 10px ;
  padding-bottom: 15px;
  top: -150px;
}
.date{
  position: relative;
  font-size: 42px;
  font-weight: 550;
  /* left: 25%; */
  text-align: center;
}
.topinfo{
  font-size: 17px;
  font-weight: 400;
  padding: 5px 12px;
}
.xuehao{
  position: relative;
  float: right;
}
.imageinfo{
  position: relative;
  /* margin: 10px 14px; */
  text-align: center;
}
.image{
  position: relative;
  height: 78%;
  /* width: 320px; */
  width: 78%;
}
.middleinfo{
  position: relative;
  text-align: center;
}
 .middleinfo1{
  padding: 5px;
}


.bottleinfo{
  margin-top: -140px;
  margin-left: 25px;
}
.bottletext{
  color: #A9A9A9;
}
.lastinfo{
  text-align: center;
  margin-top: 50px;
}
.lasttext{
  color: #1972D6;
}
</style>
