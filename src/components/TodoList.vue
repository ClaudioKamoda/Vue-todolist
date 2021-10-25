<template>
	<div class="todo-list">
		<h3>Todo List</h3>
		<input type="text" class="input-new-item" v-on:keyup.enter="addItemToList" />

		<ul>
			<li v-for="(item, index) in list" :key="index">
				<span class="list-item-check">
          <input type="checkbox" :id="index" class="item-checkbox" v-model="item.checked" />
          <label :for="index" :class="getItemClass(item.checked)">{{ item.text }}</label>
        </span>
        <span v-html="deleteIcon" @click="deleteItem(index)"></span>
			</li>
		</ul>
	</div>
</template>

<script>
import feather from 'feather-icons';

export default {
	name: 'TodoList',
	data() {
		return {
			list: []
		}
	},
	computed: {
		deleteIcon() {
			return feather.icons.trash.toSvg({width: 19});
		}
	},
	created() {
		const listOnMemory = JSON.parse(localStorage.getItem('list'))

		if (listOnMemory != null)
			//necessary check to see if it is the first time.
			this.list = listOnMemory
	},
	methods: {
		getItemClass(check) {
			return check ? 'item-checked' : '';
		},
    saveToLocalStorage(){
			localStorage.setItem('list', JSON.stringify(this.list));
    },
		addItemToList(event) {
      const newItem = event.target.value;
			this.list.push({ text: newItem, checked: false });
      this.saveToLocalStorage();
			event.target.value = '';
		},
    deleteItem(index){
      this.list.splice(index, 1);
      this.saveToLocalStorage();
    }
	}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .todo-list{
    width: 500px;
    margin: auto;
  }
  .input-new-item{
    width: 80%;
    height: 25px;
  }
  ul {
    list-style: none;
    padding: 0;
    width: 80%;
    margin: 10px auto;
    text-align: left;
  }
  li, .list-item-check{
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  .item-checkbox{
    margin-right: 10px;
  }
  .item-checked {
    text-decoration: line-through;
  }
</style>
