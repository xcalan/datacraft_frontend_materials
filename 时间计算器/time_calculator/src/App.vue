<template>
  <div id="app">
      <div>
        <input id="hour" type="text" :value="hour"> 时
        <input id="minute" type="text" :value="minute"> 分
        <input id="second" type="text" :value="second"> 秒
        &nbsp;  <input type="button" style="width:80px" value="+" @click="calculate_time()">
        &nbsp;  <input type="button" style="width:80px" value="清空" @click="clear_time()">
        <hr>
        <div id="total_time">
          total time: {{hour}}:{{minute}}:{{second}}
        </div>
      </div>
      
  </div>
</template>

<script>
export default {
  data(){
    return {
      hour:0,
      minute:0,
      second:0
    }
  },
  methods:{
    calculate_time:function(){
      let _hour = Number(document.getElementById('hour').value);
      let _minute = Number(document.getElementById('minute').value);
      let _second = Number(document.getElementById('second').value);

      if(_second + this.second >= 60){
        this.second = _second + this.second-60;
        this.minute += 1
      }else{
        this.second = _second + this.second
      }

      if(_minute + this.minute >= 60){
        this.minute = _minute + this.minute-60;
        this.hour += 1
      }else{
        this.minute = _minute + this.minute
      }

      this.hour = _hour + this.hour

    },

  clear_time:function(){
      this.hour = 0
      this.minute = 0
      this.second = 0
      document.getElementById('hour').value = 0;
      document.getElementById('minute').value = 0;
      document.getElementById('second').value = 0;
    }
  }
}
</script>


<style>

</style>
