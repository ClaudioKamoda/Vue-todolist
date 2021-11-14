<template>
	<li>
		<span class="list-item-check">
			<input
				type="checkbox"
				:id="index"
				class="item-checkbox"
				v-model="item.checked"
			/>
			<div class="content">
				<label :for="index" :class="getItemClass(item.checked)">{{
					item.text
				}}</label>
				<span class="date">Criado em: {{ item.dateCreated }}</span>
			</div>
		</span>
		<span v-html="deleteIcon" @click="deleteItem(index)"></span>
	</li>
</template>

<script>
import feather from 'feather-icons'

export default {
	name: 'ListItem',
	props: {
		item: Object,
		index: Number
	},
	computed: {
		deleteIcon() {
			return feather.icons.trash.toSvg({ width: 19 })
		}
	},
	methods: {
		getItemClass(check) {
			return check ? 'item-checked' : ''
		},
		deleteItem(index) {
			this.$emit('delete-item', index)
		}
	}
}
</script>

<style scoped>
li {
	width: 100%;
	margin-bottom: 10px;
}
li,
.list-item-check {
	display: flex;
	align-items: center;
	justify-content: space-between;
}
.item-checkbox {
	margin-right: 10px;
}
.item-checked {
	text-decoration: line-through;
}
.content {
	display: flex;
	flex-direction: column;
	align-items: flex-start;
}
.date {
	font-size: 11px;
}
</style>
