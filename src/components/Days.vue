<template>
  <div class="days">
    <div class="day">
      <div class="day__name">{{dayRender[0]}}</div>
      <div class="day__room">
        <div class="day__time"></div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'Days',
  props: ['dayRender']
}
</script>

<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
