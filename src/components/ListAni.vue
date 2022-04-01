<template>
  <div>
    <input type="text" placeholder="请输入" 
      v-model="searchText" 
      @focus="focus"
      @blur="blur"
    >
    <br>
    <input type="text" placeholder="请描述" v-model="newItem">
    <button @click="add">新增</button>
    <ul class="list" v-if="isShow">
      <li class="list-item" v-for="item, index in listItem" :key="index">{{item.title}}
        <ul class="opt-menu">
          <li class="opt-list" v-for="title, p in optList" :key="p" @click="clickHanlder(index, p)">{{title}}</li>
          <!-- <li class="opt-list" v-if="isTop" @click="toTop(index)">置顶</li>
          <li class="opt-list" v-else @click="cancelTop(index)">取消置顶</li>
          <li class="opt-list" @click="del(index)">删除</li> -->
        </ul>
      </li>
    </ul>
    <ul class="list" v-else>
      <li class="list-item" v-for="item, index in searchItem" :key="index">{{item.title}}
        <!-- <ul class="opt-menu">
          <li class="opt-list" v-for="title, p in optList" :key="p" @click="clickHanlder(index, p)">{{title}}</li>
        </ul> --> 
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      searchText: '',
      isShow: true,
      listItem: [
        {
          title: 'AAA'
        },
        {
          title: 'BBB'
        },
        {
          title: 'CCC'
        },
      ],
      optList: ['置顶', '删除'],
      searchItem: [],
      newItem: '',
    }
  },
  watch: {
    searchText() {
      let tempItem = []
      this.listItem.forEach((e) => {
        if (e.title.includes(this.searchText)) {
          tempItem.push(e);
        }
      });
      this.searchItem = new Set(tempItem);
    }
  },
  methods: {
    focus() {
      this.isShow = false;
    },
    blur() {
      this.isShow = true;
      this.searchItem = []
    },
    clickHanlder(index, p) {
      console.log('index:', index, 'p:: ', p);
      if (p === 1) {
        this.listItem.splice(index, 1)
        console.log(this.listItem);
      } else if ( p === 0) {
        let temp = this.listItem.slice(index, index + 1)
        this.listItem.splice(index,1);
        this.listItem.unshift(temp[0]);
      }
    },
    toTop(index) {
      let temp = this.listItem.slice(index, index + 1)
      this.listItem.splice(index,1);
      this.listItem.unshift(temp[0]);
    },
    cancelTop(index) {
      console.log(index)
    },
    del(index) {
      this.listItem.splice(index, 1)
    },
    add() {
      let obj = {title: this.newItem}
      this.listItem.unshift(obj)
    }
  }
}
</script>

<style scoped>
ul {
  margin: 0;
  padding: 0;
  margin-top: 20px;
  list-style: none;
}
.list-item {
  width: 100px;
  height: 30px;
  list-style: none;
  border: 1px solid #eeeeee;
  margin: 5px 0;
}
.list-item:hover .opt-menu {
  display: block;
}
.opt-menu {
  margin-left: 78px;
  text-align: center;
  padding: 5px 0;
  width: 100px;
  margin-top: -20px;
  display: none;
}
.opt-list {
  width: 100px;
  height: 30px;
}
.hight-light {
  background-color: aquamarine;
}
</style>