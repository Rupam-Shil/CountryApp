<template>
	<Header />
	<router-view />
</template>
<script>
import Header from './layout/Header';
export default {
	components: { Header },
};
</script>
<style>
*,
*::before,
*::after {
	margin: 0;
	padding: 0;
	box-sizing: border-box;
	font-family: 'Poppins', sans-serif;
}
</style>
