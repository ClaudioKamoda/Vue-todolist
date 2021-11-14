<template>
	<div class="todo-list">
		<h3>Todo List</h3>
		<input
			type="text"
			class="input-new-item"
			v-on:keyup.enter="addItemToList"
		/>

		<ul>
			<ListItem
				v-for="(item, index) in list"
				:key="index"
				:item="item"
				:index="index"
				@delete-item="deleteItem()"
			/>
		</ul>
	</div>
</template>

<script>
import ListItem from './ListItem.vue'

export default {
	name: 'TodoList',
	components: {
		ListItem
	},
	data() {
		return {
			list: []
		}
	},
	created() {
		const listOnMemory = JSON.parse(localStorage.getItem('list'))

		if (listOnMemory != null)
			//necessary check to see if it is the first time.
			this.list = listOnMemory
	},
	methods: {
		saveToLocalStorage() {
			localStorage.setItem('list', JSON.stringify(this.list))
		},
		addItemToList(event) {
			const newItem = event.target.value
			const dateNow = new Date()
			const formatedDate =
				dateNow.getDate() +
				'/' +
				(Number(dateNow.getMonth()) + 1) +
				'/' +
				dateNow.getFullYear()
			this.list.unshift({
				text: newItem,
				checked: false,
				dateCreated: formatedDate
			})
			event.target.value = ''
		},
		deleteItem(index) {
			this.list.splice(index, 1)
		}
	},
	watch: {
		list() {
			this.saveToLocalStorage()
		}
	}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.todo-list {
	width: 500px;
	margin: auto;
}
.input-new-item {
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
</style>
