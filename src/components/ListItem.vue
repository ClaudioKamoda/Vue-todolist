<template>
	<div>
		<span class="list-item-check">
			<input
				type="checkbox"
				:id="index"
				class="item-checkbox"
				v-model="item.checked"
			/>
			<label :for="index" :class="getItemClass(item.checked)">{{
				item.text
			}}</label>
		</span>
		<span v-html="deleteIcon" @click="deleteItem(index)"></span>
	</div>
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

<style scoped></style>
