<template>
  <div class="container">
    <div class="left">
      <!-- <draggable :options="{group:'people',animation:150,ghostClass:'sortable-ghost',chosenClass:'chosenClass',scroll:true,scrollSensitivity:200}" -->
      <draggable
        @change="change"
        @start="start"
        @end="end"
        :move="move"
        :options="{handle: '#title', animation: 60}"
        >
        <!-- style="display: inline-block; width:190px;height: 600px;background: #eee;overflow: auto"> -->
        <!-- <li v-for="(item, index) in list2" :class="setclass(item,index)" :key="index">{{item.name}}</li> -->
        <!-- <transition-group> -->
          <div id="1" class="one leftModule">
              <div id="title">标题1</div>1
          </div>
          <div id="2" class="one leftModule">
            <div id="title">标题2</div>2
          </div>
          <div id="3" class="one leftModule">
            <div id="title">标题3</div>3
          </div>
          <div id="4" class="one leftModule">
            <div id="title">标题4</div>4
          </div>
        <!-- </transition-group> -->
      </draggable>
    </div>

    <div class="right">
      <draggable
        @change="change"
        @start="start"
        @end="end"
        :move="move"
        >
        <div id="5" class="one rightModule">
            <div id="title">标题5</div>5
        </div>
        <div id="6" class="one rightModule">
            <div id="title">标题6</div>6
        </div>
        <div id="7" class="one rightModule">
            <div id="title">标题7</div>7
        </div>
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
      // list1Id: [],
      // list2Id: []
      leftIds: [],
      rightIds: [],
      allIds: []
    }
  },
  methods: {
    // evt里面有两个值，一个evt.added 和evt.removed  可以分别知道移动元素的ID和删除元素的ID
    change: function (evt) {
      console.log('触发了change事件')
      console.log(evt)
    },
    // start ,end ,add,update, sort, remove 得到的都差不多
    start: function (evt) {
      console.log('触发了start事件')
      console.log(evt)
    },
    end: function (evt) {
      console.log('触发了end事件')
      console.log(evt)
      this.getIds()
      // console.log('this.list1Id:', this.list1Id)
      // evt.item // 可以知道拖动的本身
      // evt.to    // 可以知道拖动的目标列表
      // evt.from  // 可以知道之前的列表
      // evt.oldIndex  // 可以知道拖动前的位置
      // evt.newIndex  // 可以知道拖动后的位置
    },
    move: function (evt, originalEvent) {
      console.log('触发了move事件')
      console.log(evt)
      console.log(originalEvent) // 鼠标位置
    },
    getIds () {
      const leftBoxs = document.querySelectorAll('.left .leftModule')
      const rightBoxs = document.querySelectorAll('.right .rightModule')
      this.leftIds = []
      this.rightIds = []
      for (let i = 0; i < leftBoxs.length; i++) {
        this.leftIds.push(leftBoxs[i].id)
      }
      for (let i = 0; i < rightBoxs.length; i++) {
        this.rightIds.push(rightBoxs[i].id)
      }
      this.allIds = this.leftIds.concat(this.rightIds)
      console.log('this.leftIds:', this.leftIds)
      console.log('this.rightIds:', this.rightIds)
      console.log('this.allIds:', this.allIds)
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
.one {
  border: 1px solid red;
  width: 100%;
  height: 100px;
  /* padding: 10px; */
  box-sizing: border-box;
}
#title {
  height: 30px;
  background: pink;
  cursor: move;
}
.ghost {
  opacity: 0.5;
  background: #c8ebfb;
}
</style>
