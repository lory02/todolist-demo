<template>
  <view class="container">
    <view class="todo-input-view uni-form-item uni-column">
      <view class="uni-input-wrapper">
        <input @confirm="addTodo" v-model="inputText" class="uni-input" placeholder="请输入Todo" />
      </view>
    </view>

    <view class="todo-view">
      <view class="todo-item" v-for="(item, index) in todoList " :key="index">
        <checkbox @click="modifyCheck(item)" :checked="item.checked" />
        <text>{{ item.text }}</text>
        <!-- <text class="star" @click="modifyStar(item)">{{ item.star ? '收藏':'未收藏'}}</text> -->
        <image class="star-svg" @click="modifyStar(item)" :src="getStarSvg(item)" />
      </view>
    </view>

    <!-- <image class="star-svg" src="/static/icon/xingxing_1.svg" /> -->
  </view>
</template>

<script>
  export default {
    data() {
      return {
        star0: '/static/icon/xingxing_0.svg',
        star1: '/static/icon/xingxing_1.svg',
        inputText: '',
        todoList: [{
          text: "已完成的todo",
          star: false,
          checked: true
        }],
      }
    },
    methods: {
      addTodo() {
        const newData = {
          text: this.inputText,
          star: false,
          checked: false
        };
        this.todoList.push(newData);
        this.inputText = ''
      },
      modifyStar(item) {
        item.star = !item.star
      },
      modifyCheck(item) {
        item.checked = !item.checked
      },
      getStarSvg(item) {
        return item.star ? this.star1 : this.star0
      }
    },
  }
</script>

<style>
  .container {
    padding: 20px;
    font-size: 14px;
    line-height: 24px;
  }

  .todo-input-view {
    margin-bottom: 20px;
  }

  .todo-item {
    display: -webkit-flex;
    display: flex;
  }

  .star {
    margin-left: auto;
  }

  .star-svg {
    margin-left: auto;
    width: 1.5em;
    height: 1.5em;
    vertical-align: -0.15em;
    fill: currentColor;
    overflow: hidden;
  }

</style>
