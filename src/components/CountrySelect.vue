<template>
	<select @change="onChange()" v-model="selected" place>
		<option value="" disabled selected>Filter By Regions..</option>
		<option v-for="(region, i) in regions" :key="i" :value="region">{{
			region
		}}</option>
	</select>
</template>

<script>
export default {
	data() {
		return {
			selected: '',
		};
	},
	props: ['regions'],
	methods: {
		onChange() {
			this.$emit('changedRegion', this.selected);
		},
	},
};
</script>

<style>
select {
	width: 12rem;
	height: 2.5rem;
	outline: none;
	border: none;
	box-shadow: 0px 7px 7px 0px rgba(201, 201, 201, 0.75);
	-webkit-box-shadow: 0px 7px 7px 0px rgba(201, 201, 201, 0.75);
	-moz-box-shadow: 0px 7px 7px 0px rgba(201, 201, 201, 0.75);
	padding: 0 1rem;
}

option {
	padding: 1rem;
}
</style>
