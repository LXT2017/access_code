<template>
<div>
  <div class="body1">
    <div class="top">请输入相应的学生信息</div>

    
    <div class="middle">
      <div class="info"> 您的身份：</div>
    <select v-model="id" class="input">
        <option  v-for="item in couponList" :key="item.id" :value="item.id">{{item.name}}</option>
    </select>
    <div class="info"> 学院：</div>
    <input class="input" v-model="college">s
    <div class="info"> 学号：</div>
    <input class="input" v-model="number">
    <div class="info"> 姓名：</div>
    <input class="input" v-model="name">
    </div>
    <div class="btn" @click="btn">
      提交
    </div>
  </div>
</div>
</template>

<script>
export default {
  data() {
    return {
      id:'',
      college:'',
      number:'',
      name: '',
      couponList:[
          {
              id: '0',
              name: '本科生'
          },
          {
              id: '1',
              name: '研究生'
          }]
    }
  },
  methods:{
    btn(){
      if(this.number==''||this.college==''||this.name==''||this.id==''){
        alert("请填写正确的信息");
        return;
      }
      localStorage.setItem("college",this.college);
      localStorage.setItem("number",this.number);
      localStorage.setItem("name",this.name);
      localStorage.setItem("id",this.id);
      this.$router.push("/info")
    }
  }
}
</script>

<style scoped>
body {
  padding: 0;
  margin: 0;
}
.body1{
  background: url("../assets/bac.jpg");
  width: 100%;
  height: 100%;
  position: fixed;
  background-size: 100% 100%;
  z-index: 0;
  opacity: 0.95;
}
.top{
  color: red;
  font-size: 25px;
  margin: 10px;
  text-align: center;
}
.info{
  color: red;
  font-size: 25px;
  margin: 10px;
}
.middle{
  text-align: center;
  position: relative;
  margin: 20px;
}
.input{
  font-size: 25px;
  width: 100%;
  height: 30px;
  border: 0;
  border-radius: 5px;
}
.btn{
  text-align: center;
  font-size: 30px;
  background-color: red;
  opacity: 0.9;
  margin: 5px 20px;
  border-radius: 6px;
  z-index: 9;
}
</style>