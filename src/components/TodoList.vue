<template>
  <div class="todo-list">
    <h3>Todo List</h3>
    <input type="text" v-on:keyup.enter="addItemToList">

    <ul>
      <li v-for="(item, index) in list" :key="index">
        <input type="checkbox" v-model="item.checked">
        <span :class="getItemClass(item.checked)">{{item.text}}</span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'TodoList',
  data(){
    return{
      list: []
    }
  },
  created(){
    const listOnMemory = JSON.parse(localStorage.getItem('list'));
    
    if(listOnMemory != null) //necessary check to see if it is the first time.
      this.list = listOnMemory;
  },
  methods: {
    getItemClass(check){
      return check ? 'item-checked' : '';
    },
    addItemToList(event){
      const newItem = event.target.value;
      this.list.push({text: newItem, checked: false});
      localStorage.setItem('list', JSON.stringify(this.list));
      event.target.value = '';
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  ul{
    list-style: none;
    padding: 0;
  }
  .item-checked{
    text-decoration: line-through;
  }
</style>
