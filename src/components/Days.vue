<template>
  <div class="days">
    <div class="day" v-for="day in dayRender">
      <div class="day__name">{{day[0]}}</div>
      <div class="day__room" v-for="(room, typeRoom) in day[1]">
        <div 
        class="day__time" 
        v-bind:data-value="time" 
        v-bind:class="'day__time--' + time"
        v-bind:data-way="[key, typeRoom,day[0]]" 
        v-for="(time, key) in room" 
        v-on:click="changeValueRoom">{{key}}
      </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'Days',
  props: ['dayRender'],
  methods: {
    changeValueRoom: function() {
      let way = event.target.dataset.way;
      this.$emit('changevalueroom', way);
    }
  }
}
</script>

<style scoped>
.days {
  display: flex;
  justify-content: space-between;
}

.day {
  width: 20%;
}

.day__name {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 50px;
  border-right: 1px solid #eaeaea;
  font-size: 15px;
}

.day:first-child .day__name{
  border-left: 1px solid #eaeaea;
}

.day__room {
  display: flex;
  flex-wrap: wrap;
  height: 100px;
  margin: 0 0 10px 0;
  border: 1px solid #eaeaea;
  border-left: none;
  box-sizing: border-box;
}

.day__time {
  display: flex;
  align-items: center;
  width: calc(50% - 10px);
  padding: 0px 5px;
  font-size: 12px;
  position: relative;
  cursor: pointer;
}

.day__time--free {
  background-color: #fff;
}

.day__time--false {
  background-color: #eaeaea;
}

.day__time:after {
  content: "+";
  position: absolute;
  top: 1px;
  right: 20px;
  font-size: 14px;
}

.day__time:hover {
  background-color: #f6f6f6;
}
</style>
