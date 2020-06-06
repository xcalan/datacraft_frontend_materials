<template>
  <div id="app">
    <div>
      <input id="hour" type="number" v-model:value="hour"> 时
      <input id="minute" type="number" v-model:value="minute"> 分
      <input id="second" type="number" v-model:value="second"> 秒
      &nbsp;
      <input type="button" style="width:80px" value="+" @click="calculate_time()">
      &nbsp;
      <input type="button" style="width:80px" value="清空" @click="clear_time()">
      <hr>
      <div id="total_time">total time: {{total_hour}}:{{total_minute}}:{{total_second}}</div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      hour: 0,
      minute: 0,
      second: 0,
      total_hour: 0,
      total_minute: 0,
      total_second: 0
    };
  },
  methods: {
    calculate_time() {
      if (
        Number(this.second) < 60 &&
        this.total_second + Number(this.second) < 60
      ) {
        this.total_second += Number(this.second);
      } else if (Number(this.second) >= 60) {
        this.second = 0;
        alert("秒数不能超过60s，请重新输入");
      } else {
        this.total_second = this.total_second + Number(this.second) - 60;
        this.total_minute += 1;
      }

      if (
        Number(this.minute) < 60 &&
        this.total_minute + Number(this.minute) < 60
      ) {
        this.total_minute += Number(this.minute);
      } else if (Number(this.minute) >= 60) {
        this.minute = 0;
        alert("分钟数不能超过60min，请重新输入");
      } else {
        this.total_minute = this.total_minute + Number(this.minute) - 60;
        this.total_hour += 1;
      }

      this.total_hour += Number(this.hour);

      this.hour = 0;
      this.minute = 0;
      this.second = 0;
    },

    clear_time: function() {
      this.hour = 0;
      this.minute = 0;
      this.second = 0;
      this.total_hour = 0;
      this.total_minute = 0;
      this.total_second = 0;
    }
  }
};
</script>


<style>
</style>
