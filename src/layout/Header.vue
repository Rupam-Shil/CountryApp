<template>
	<nav>
		<h1>Where in the world?</h1>
		<button class="myBtn" @click="toggleMode">
			<div class="nav__dark" v-if="!dark">
				<p><i class="uil uil-moon nav__icon"></i>Dark Mode</p>
			</div>
			<div class="nav__dark" v-else>
				<p><i class="uil uil-sun nav__icon"></i>Light Mode</p>
			</div>
		</button>
	</nav>
</template>

<script>
export default {
	data() {
		return {
			dark: false,
		};
	},
	methods: {
		toggleMode() {
			if (!this.dark) {
				this.dark = true;
			} else {
				this.dark = false;
			}
		},
	},
};
</script>

<style>
.myBtn {
	border: none;
	background-color: transparent;
}
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
@media only screen and (max-width: 968px) {
	nav {
		padding: 1rem 2rem;
	}
}
@media only screen and (max-width: 816px) {
}
@media only screen and (max-width: 517px) {
	nav {
		padding: 1rem 1rem;
	}
	.nav__dark:hover {
		transform: translateX(-0.5rem);
	}
}
</style>
