<template>
	<nav>
		<h1>Where in the world?</h1>
		<div class="nav__dark">
			<p><i class="uil uil-moon nav__icon"></i>Dark Mode</p>
		</div>
	</nav>
</template>

<script>
export default {};
</script>

<style>
nav {
	width: 100vw;
	padding: 1rem 4rem;
	font-weight: 500;
	height: 4rem;
	background: #fff;
	box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
	display: flex;
	justify-content: space-between;
	align-items: center;
}
.nav__dark {
	display: block;
	transition: 0.2s;
	cursor: pointer;
}
.nav__dark:hover {
	transform: translateX(0.5rem);
}
.nav__icon {
	margin-right: 0.5rem;
}
</style>
