<template>
  <div id="list-demo" class="list-demo">
    <!-- <button v-on:click="shuffle">Shuffle</button> -->
    <div class="list-btn">
      <button v-on:click="add">Add</button>
      <button v-on:click="remove">Remove</button>
    </div>
    <div class="list">
      <transition-group name="list-complete" tag="div">
        <div
          v-for="item in listData"
          :key="item"
          class="list-complete-item"
        >
          {{ item }}
        </div>
      </transition-group>
    </div>
  </div>  
</template>

<script>
export default {
  data() {
    return {
      listData: [1,2,3,4,5,6,7,8,9],
      // listData: ['这是一条消息','这是一条消息'],
      nextNum: 10
    }
  },
  methods: {
    randomIndex() {
      return Math.floor(Math.random() * this.listData.length);
    },
    add() {
      this.listData.splice(this.randomIndex(), 0, this.nextNum++)
    },
    remove() {
      this.listData.splice(this.randomIndex(), 1)
    },
    // shuffle() {
    //   this.listData = _.shuffle(this.listData)
    // }
  }

}
</script>

<style>
.list-demo {
  padding: 20px;
  height: 800px;
  width: 800px;
}
.list-btn {
  margin-right: 10px;
  display: flex;
  justify-content: space-evenly;
}
.list-btn button {
  width: 65px;
  height: 25px;
}
.list {
  margin-top: 20px;
  border: 1px solid #ccc;
  height: 530px;
  overflow: auto;
}
.list-complete-item {
  margin-left: 220px;
  padding: 10px;
  width: 180px;
  height: 26px;
  border-bottom: 1px solid #fff;
  border-radius: 3px;
  background: #eee;
}
.list-complete-item:hover {
  background-color: #ddd;
}
.list-complete-enter, 
.list-complete-leave-to {
  opacity: 0;
  transform: translateX(-100%);
}
.list-complete-enter-active,
.list-complete-leave-active {
  transition: all .4s cubic-bezier(.25, .1, .25, 1);
}
.list-complete-move {
  transition: all .4s cubic-bezier(.25, .1, .25, 1);
}
.list-complete-leave-active {
  position: absolute;
}
</style>