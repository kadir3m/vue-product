<template>
  <div class="progressbar">
    <span :style="{color: percentage > 50 ? 'white' : ''}">{{percentage+'%'}}</span>

    <div class="active" :style="{width: percentage + '%'}">
<p></p>
<p></p>
<p></p>
    </div>
  </div>
</template>

<script>
export default {
  props: ['percentage'],
    watch: {
    percentage: function (value) {
    console.log("list =>", value)
    console.log("2")
    }
    }
};
</script>

<style scoped>
.progressbar {

  height: 30px;
  background-color: rgb(213, 213, 213);
  border-radius: 6px;
  display: flex;
  margin: 30px;
}
.progressbar .active {
      width: 0%;
    height: 30px;
    background-color: rgb(213, 213, 213);
    border-radius: 6px;
    display: flex;
    align-items: center;
    width: 100;
    background-color: blue;
    transition: all 1s ease;

}
.progressbar span {
  align-self: center;
    left: 50%;
    position: absolute;
    justify-self: center;
    right: 50%;
}
</style>
