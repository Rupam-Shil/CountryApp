<template>
	<select>
		<option value="0">Filter By Region</option>
		<option v-for="country in countries" :key="country.latlng[0]">{{
			country.region
		}}</option>
	</select>
</template>

<script>
export default {
	data() {
		return {};
	},
	props: ['countries'],
};
</script>

<style>
select {
	width: 10rem;
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
