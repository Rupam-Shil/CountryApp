<template>
	<section>
		<form @click.prevent="">
			<div class="search__country">
				<div class="serach__icon">
					<i class="uil uil-search-alt"></i>
				</div>
				<input type="text" placeholder="Search for a country..." />
			</div>
			<CountrySelect :countries="countries" />
		</form>
		{{ countries }}
	</section>
</template>

<script>
import CountrySelect from '../components/CountrySelect';
export default {
	name: 'Home',
	data() {
		return {
			countries: [],
			regions: [],
		};
	},
	methods: {
		async fetchCountries() {
			const res = await fetch('https://restcountries.eu/rest/v2/all');
			const data = await res.json();
			return data;
		},
	},
	async created() {
		const data = await this.fetchCountries();
		//TODO:ADD region
	},
	components: { CountrySelect },
};
</script>
<style>
body {
	background: rgb(240, 240, 240);
}
section {
	margin-top: 2rem;
	width: 100%;
	padding: 0 4rem;
}
form .search__country {
	height: 2.5rem;
	box-shadow: 0px 7px 7px 0px rgba(201, 201, 201, 0.75);
	-webkit-box-shadow: 0px 7px 7px 0px rgba(201, 201, 201, 0.75);
	-moz-box-shadow: 0px 7px 7px 0px rgba(201, 201, 201, 0.75);
	display: flex;
}
.serach__icon {
	width: 2.5rem;
	height: 100%;
	border-top-left-radius: 0.2rem;
	border-bottom-left-radius: 0.2rem;
	background: #fff;
	display: grid;
	place-items: center;
}
form input {
	background: #fff;
	height: 100%;
	width: 20rem;
	outline: none;
	border: none;
	border-top-right-radius: 0.2rem;
	border-bottom-right-radius: 0.2rem;
}
form {
	display: flex;
	justify-content: space-between;
	align-items: center;
}
</style>
