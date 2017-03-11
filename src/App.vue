<template>
  <div id="app">
    <p>{{information.name}}</p>
    <p>{{information.time}}</p>
    <ul>
      <li v-for="message in messages">
        <p v-text="message.name"></p>
        <p v-text="message.message"></p>
        <p v-text="message.time"></p>
      </li>
    </ul>
    <textarea v-model="newMessage.message"></textarea>
    <button type="button" @click="add()">提交</button>
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: 'app',
  data() {
    return {
        messages: [],
        information : {
            name : '胖砸',
            time : new Date()
        },
        newMessage: {
            name: '',
            time: '',
            message: ''
        }
    }
  },
  mounted :function() {
    this.getInformation();
  },
  methods: {
    add : function() {
        console.log(this)
        this.newMessage.time = new Date();
        this.messages.push(this.newMessage)
    },
    getInformation : function() {
        this.newMessage.name = this.information.name;
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
