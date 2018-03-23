<template>
  <div id="app">
    <div class="form">
      <h1>Бронирование переговорок</h1>
      <div class="form-left">
        <div class="form-left__cell form-left__cell--top">
          <div class="form-left__title">Комната</div>
        </div>
        <div class="form-left__cell">
          <div class="form-left__title">Зеленая</div>
          <div class="form-left__description">(до 5 персон)</div>
        </div>
        <div class="form-left__cell">
          <div class="form-left__title">Красная</div>
          <div class="form-left__description">(до 15 персон)</div>
        </div>
        <div class="form-left__cell">
          <div class="form-left__title">Синяя</div>
          <div class="form-left__description">(до 25 персон)</div>
        </div>
        <div class="form-left__cell">
          <div class="form-left__title">Фиолетовая</div>
          <div class="form-left__description">(до 25 персон)</div>
        </div>
      </div>
      <div class="form-right">
        <DayHeader v-bind:name-month="nameOfMonth"></DayHeader>
        <Days v-bind:day-render="dayRender"></Days>
      </div>
      <!--<div class="form-right">
        <header class="days-header">
          <div class="days-header__arrow days-header__arrow--left"></div>
            <div class="days-header__name">Апрель</div>
          <div class="days-header__arrow days-header__arrow--right"></div>
        </header>
        <div class="days">
          <div class="day">
            <div class="day__name">10 Понедельник</div>
            <div class="day__room">
              <div class="day__time">09:00</div>
              <div class="day__time">10:00</div>
              <div class="day__time">11:00</div>
              <div class="day__time">12:00</div>
              <div class="day__time">13:00</div>
              <div class="day__time">14:00</div>
              <div class="day__time">15:00</div>
              <div class="day__time">16:00</div>
              <div class="day__time">17:00</div>
              <div class="day__time">18:00</div>
            </div>
          </div>
        </div>
      </div>-->
    </div>
  </div>
</template>

<script>

let startDate = {
  Апрель: {
    "02 Понедельник": {},
    "03 Вторник": {},
    "04 Среда": {},
    "05 Четверг": {},
    "06 Пятница": {},
    "09 Понедельник": {},
    "10 Вторник": {},
    "11 Среда": {},
    "12 Четверг": {},
    "13 Пятница": {},
    "16 Понедельник": {},
    "17 Вторник": {},
    "18 Среда": {},
    "19 Четверг": {},
    "20 Понедельник": {},
    "23 Пятница": {},
    "24 Вторник": {},
    "25 Среда": {},
    "26 Четверг": {},
    "27 Пятница": {},
    "28 Суббота": {},
  }
}

let startColorRooms = {
  Зеленая: {},
  Красная: {},
  Синяя: {},
  Фиолетовая: {}
}

const startTime = {
  "09:00": "free",
  "10:00": "free",
  "11:00": "free",
  "12:00": "free",
  "13:00": "free",
  "14:00": "free",
  "15:00": "free",
  "16:00": "free",
  "17:00": "free",
  "18:00": "free"
}

import Days from './components/Days';
import DayHeader from './components/DayHeader';

export default {
  name: 'App',
  components: {
    Days,
    DayHeader
  },

  data () {
    return {
      startDate: startDate,
      dayRender: [],
      keysStartDate: [],
      indexWeek: Number,
      nameOfMonth: ""
    }
  },

  created: function() {
    this.createRoomTime;
    this.createSchedule;
    this.startDaysRender;
    this.startRenderDate();
  },

  computed: {
    createRoomTime: function() {
      for (let time in startColorRooms) {
        startColorRooms[time] = startTime;
      }
    },

    createSchedule: function() {
      
      for (let key in this.startDate) {
        this.keysStartDate = Object.keys(this.startDate[key]);

        this.nameOfMonth = key;

        for (let key in this.startDate) {
          let lastObj = this.startDate[key];

          for (let day in lastObj) {
            lastObj[day] = startColorRooms;
          }
        }
      }
      
    },

    startDaysRender: function() {
      this.indexWeek = 0;
      let monthForRender = {};
      let indexForRenderArr = this.keysStartDate.slice(this.indexWeek, 5);

     // console.log(this.startDate.key);

      for (let key in this.startDate) {
        monthForRender = this.startDate[key];
      }

      for (let i = 0; i < indexForRenderArr.length; i++){
        for (let days in monthForRender) {
          if(indexForRenderArr[i] === days) {
            this.dayRender.push(monthForRender[days]);
          }
        }
      }
    }
  },

  methods: {
    startRenderDate: function() {
     // console.log(this.dayRender);
    }
  }
}
</script>

<style>
body {
  display: flex;
  justify-content: center;
  margin: 0 auto;
  font-family: sans-serif;
  color: #333333;
}

#app {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  width: 100%;
  margin-top: 60px;
}

h1 {
  width: 100%;
  margin-bottom: 40px;
}

.form {
  display: flex;
  flex-wrap: wrap;
  width: 100%;
  max-width: 960px;
}

.form-left {
  width: 25%;
}

.form-left__title {
  width: 100%;
  font-size: 18px;
  font-weight: 600;
}

.form-left__cell {
  display: flex;
  align-content: flex-start;
  flex-wrap: wrap;
  height: 100px;
  margin: 0 0 10px 0;
  padding: 15px;
  border: 1px solid #eaeaea;
}

.form-left__cell--top {
  border: none;
}

.form-right {
  width: 75%;
}

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
  height: 75px;
  font-size: 15px;
}

.day__room {
  display: flex;
  flex-wrap: wrap;
  height: 100px;
  margin: 0 0 10px 0;
  border: 1px solid #eaeaea;
  border-left: none;
}

.day__time {
  display: flex;
  align-items: center;
  width: 50%;
  padding: 0px 5px;
  font-size: 12px;
  position: relative;
  cursor: pointer;
}

.day__time:after {
  content: "+";
  position: absolute;
  top: -2px;
  right: 20px;
  font-size: 14px;
}

.day__time:hover {
  background-color: #f6f6f6;
}


</style>
