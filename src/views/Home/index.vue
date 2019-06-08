<template>
  <div class="container">
    <div class="left">
      <div class="one">
        1
      </div>
      <div class="two">
        2
      </div>
      <div class="three">
        3
      </div>
      <div class="four">
        4
      </div>
    </div>

    <div class="right">
      <div class="five">
        5
      </div>
      <div class="six">
        6
      </div>
      <div class="seven">
        7
      </div>
    </div>

  </div>
</template>
<script>
</script>
<style scoped>
.container {
  width: 500px;
}
.left {
  width: 50%;
  height: 100%;
  border: 1px solid purple;
  float: left;
  box-sizing: border-box;
  padding: 10px;
}
.right {
  width: 50%;
  height: 100%;
  border: 1px solid blue;
  float: right;
  box-sizing: border-box;
  padding: 10px;
}
.one, .two, .three, .four, .five, .six, .seven {
  border: 1px solid red;
  width: 100%;
  height: 100px;
  padding: 10px;
  box-sizing: border-box;
}
</style>
