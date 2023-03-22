<template>
  <view class="container">
    <view class="uni-form-item uni-column">
      <view class="uni-input-wrapper">
        <input @confirm="addTodo" v-model="inputText" class="uni-input" placeholder="请输入Todo" />
      </view>
    </view>

    <view class="todo-view">
      <view v-for="(item, index) in todoList " :key="index">
        <checkbox @click="modifyCheck(item)" :checked="item.checked" />
        <text>{{ item.text }}</text>
        <text class="star" @click="modifyStar(item)">{{ item.star ? '收藏':'未收藏'}}</text>
      </view>
    </view>
  </view>
</template>

<script>
  export default {
    data() {
      return {
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
        let newData = {
          text: this.inputText,
          star: false,
          checked: false
        };
        this.todoList.push(newData);
        this.inputText = ''
        console.log(this.todoList)
        console.log(this.inputText)
      },
      modifyStar(item) {
        item.star = !item.star
      },
      modifyCheck(item) {
        item.checked = !item.checked
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

  .todo-view .star {
    margin-left: 70px;
  }
</style>
