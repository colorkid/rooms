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
        <DayHeader v-bind:data-for-header="dataForHeader" v-on:changeday="changeDay"></DayHeader>
        <Days v-bind:day-render="dayRender" v-on:changevalueroom="changeValueRoom"></Days>
      </div>
    </div>
  </div>
</template>

<script>

let startDate = {
  Апрель: {
    "01 Воскресенье": {},
    "02 Понедельник": {},
    "03 Вторник": {},
    "04 Среда": {},
    "05 Четверг": {},
    "06 Пятница": {},
    "07 Суббота": {},
    "08 Воскресенье": {},
    "09 Понедельник": {},
    "10 Вторник": {},
    "11 Среда": {},
    "12 Четверг": {},
    "13 Пятница": {},
    "14 Суббота": {},
    "15 Воскресенье": {},
    "16 Понедельник": {},
    "17 Вторник": {},
    "18 Среда": {},
    "19 Четверг": {},
    "20 Пятница": {},
    "21 Суббота": {},
    "22 Воскресенье": {},
    "23 Понедельник": {},
    "24 Вторник": {},
    "25 Среда": {},
    "26 Четверг": {},
    "27 Пятница": {},
    "28 Суббота": {},
    "29 Воскресенье": {},
    "30 Понедельник": {}
  }
}

//СДЕЛАТЬ ОБЪЕКТ С ДАТАМИ ДЛИННОЙ ЧТОБ ОНА ДЕЛИЛАСЬ БЕЗ ОСТАТКА НА 5, ПРИ ЛЮБЫХ ВХОДНЫХ ДАННЫХ

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
      dataForHeader: {
        dayFrom: 0,
        dayTo: 5,
        nameOfMonth: "",
        keysStartDatelength: Number
      },
      wayToData: {}
    }
  },

  created: function() {
    this.createRoomTime;
    this.createSchedule;
    this.renderDays;
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

        this.dataForHeader.keysStartDatelength = this.keysStartDate.length;
        this.dataForHeader.nameOfMonth = key;

        for (let key in this.startDate) {
          let lastObj = this.startDate[key];

          for (let day in lastObj) {
            lastObj[day] = startColorRooms;
          }
        }
      }
      
    },

    renderDays: function() {
      let monthForRender = {};
      let indexForRenderArr = this.keysStartDate.slice(this.dataForHeader.dayFrom, this.dataForHeader.dayTo);

      this.dayRender = [];

      for (let key in this.startDate) {
        monthForRender = this.startDate[key];
      }

      for (let i = 0; i < indexForRenderArr.length; i++){
        for (let days in monthForRender) {
          if (indexForRenderArr[i] === days) {
            this.dayRender.push([indexForRenderArr[i], monthForRender[days]]);
          }
        }
      }
    }
  },

  methods: {
    startRenderDate: function() {
     // console.log(this.dayRender);
    },

    changeDay: function(dayFrom, dayTo) {

      this.dataForHeader.dayFrom = dayFrom;
      this.dataForHeader.dayTo = dayTo;

      this.renderDays;
    },

    changeValueRoom: function(way) {
      let wayArr = way.split(',');

      this.wayToData.time = wayArr[0];
      this.wayToData.color = wayArr[1];
      this.wayToData.day = wayArr[2];

      this.changeStateOfRoom(this.wayToData.day, this.wayToData.color, this.wayToData.time);
    },

    changeStateOfRoom: function(day, color, time) {
      for (let day in this.startDate) {
        let ourDayObj = this.startDate[day];
        for (let dayInMonth in ourDayObj) {
          if (dayInMonth === this.wayToData.day) {
            let objOurDay = ourDayObj[dayInMonth];
            for (let color in objOurDay) {
              if (color === this.wayToData.color) {
                let timeInRomm = objOurDay[color];
                for (let time in timeInRomm) {
                  if (time === this.wayToData.time) {
                    timeInRomm[time] = "false";
                  }
                }
              }
            }
          }
        }
      }

     console.log(this.startDate);

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
  box-sizing: border-box;
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
  box-sizing: border-box;
}

.form-left__cell--top {
  height: 75px;
  border: none;
}

.form-right {
  width: 75%;
}




</style>
