<template>
  <div class="container">
    <div class="left">
      <!-- <draggable :options="{group:'people',animation:150,ghostClass:'sortable-ghost',chosenClass:'chosenClass',scroll:true,scrollSensitivity:200}" -->
      <draggable
        v-model="list2"
        @change="change"
        @start="start"
        @end="end"
        :move="move"
        >
        <!-- style="display: inline-block; width:190px;height: 600px;background: #eee;overflow: auto"> -->
        <!-- <li v-for="(item, index) in list2" :class="setclass(item,index)" :key="index">{{item.name}}</li> -->
        <!-- <transition-group> -->
          <div class="one">1</div>
          <div class="two">2</div>
          <div class="three">3</div>
          <div class="four">4</div>
        <!-- </transition-group> -->
      </draggable>
    </div>

    <div class="right">
      <draggable
        v-model="list2"
        @change="change"
        @start="start"
        @end="end"
        :move="move"
        >
        <div class="five">5</div>
        <div class="six">6</div>
        <div class="seven">7</div>
      </draggable>
    </div>

  </div>
</template>
<script>
import draggable from 'vuedraggable'

export default {
  components: { draggable },
  data () {
    return {

    }
  },
  methods: {
    // evt里面有两个值，一个evt.added 和evt.removed  可以分别知道移动元素的ID和删除元素的ID
    change: function (evt) {
      console.log(evt)
    },
    // start ,end ,add,update, sort, remove 得到的都差不多
    start: function (evt) {
      console.log(evt)
    },
    end: function (evt) {
      console.log(evt)
      // evt.item // 可以知道拖动的本身
      // evt.to    // 可以知道拖动的目标列表
      // evt.from  // 可以知道之前的列表
      // evt.oldIndex  // 可以知道拖动前的位置
      // evt.newIndex  // 可以知道拖动后的位置
    },
    move: function (evt, originalEvent) {
      console.log(evt)
      console.log(originalEvent) // 鼠标位置
    }
  }
}

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
