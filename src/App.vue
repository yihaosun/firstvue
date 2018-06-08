<template>
  <div id="app">
    <!--<img src="./assets/logo.png">-->
    <!--<hello></hello>-->
    <!--如果要使用这个hello标签，就必须要在script中注册一下，才能使用。-->
    <h1 v-text="title"></h1>
    <input v-model="newItem" v-on:keyup.enter="addItem">
    <ul>
      <li v-for="item in items" style="list-style: none" v-bind:class="{fisnined:item.isFishined}" v-on:click="onClickFinished(item)">
        {{item.label}}
      </li>
    </ul>
  </div>
</template>

<script>
import hello from './components/HelloWorld.vue'
export default {
    //export 相当于new vue({})的作用
  name: 'App',
//  components:{
//      hello
//  }
  data:function () {
    return {
        title:"要做的事情",
        items:[

        ],
      newItem:''
    }
  },
  //这是方法执行
  methods:{
    onClickFinished:function(item){
      item.isFishined=!item.isFishined;
    },
    addItem:function () {
      console.log(this.newItem);
      this.items.push({
        label:this.newItem,
        isFishined:false
      });
      //这里就体现出了v-model的数据双向绑定
      this.newItem=""
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
.fisnined{
  text-decoration: underline;
}
</style>
