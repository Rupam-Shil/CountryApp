<template>
	<section>
		<form @click.prevent="">
			<div class="search__country">
				<div class="serach__icon">
					<i class="uil uil-search-alt"></i>
				</div>
				<input
					type="text"
					placeholder="Search for a country..."
					v-model="inputSearch"
					@input="search"
				/>
			</div>
			<CountrySelect @changedRegion="filterCountry" :regions="regions" />
		</form>
	</section>
	<div class="containerBox">
		<CountryCard
			v-for="country in countries"
			:key="country.callingCodes"
			:country="country"
		/>
	</div>
</template>

<script>
import CountrySelect from '../components/CountrySelect';
import CountryCard from '../components/CountryCard';
export default {
	name: 'Home',
	data() {
		return {
			countries: [],
			regions: [],
			inputSearch: '',
		};
	},
	methods: {
		async fetchCountries() {
			const res = await fetch('https://restcountries.eu/rest/v2/all');
			const data = await res.json();
			return data;
		},
		async filterCountry(c) {
			const data = await this.fetchCountries();
			this.countries = data;
			this.countries = this.countries.filter((country) => {
				return country.region === c;
			});
		},
		async search() {
			const data = await this.fetchCountries();
			this.countries = data;
			this.countries = this.countries.filter((country) => {
				return country.name.toLowerCase().includes(this.inputSearch);
			});
		},
	},
	async created() {
		const data = await this.fetchCountries();
		this.countries = data;
		this.countries.forEach((country) => {
			this.regions.push(country.region);
		});
		this.regions = [...new Set(this.regions)];
		this.regions.pop();
	},
	components: { CountrySelect, CountryCard },
	emits: ['changedRegion'],
};
</script>
<style>
body {
	background: rgb(240, 240, 240);
	overflow-x: hidden;
}
section {
	margin-top: 2rem;
	width: 100%;
	padding: 0 4rem;
	margin-bottom: 3rem;
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

.containerBox {
	padding: 0 4rem;
	display: grid;
	grid-template-columns: repeat(4, 1fr);
	row-gap: 3rem;
	margin-bottom: 3rem;
	place-items: center;
}
@media only screen and (max-width: 968px) {
	section {
		padding: 0 2rem;
		margin-bottom: 3rem;
	}
	.containerBox {
		padding: 0 2rem;

		grid-template-columns: repeat(3, 1fr);
	}
}
@media only screen and (max-width: 816px) {
	body {
		font-size: 12px;
	}
	section {
		padding: 0 1rem;
		margin-bottom: 3rem;
	}
	.containerBox {
		padding: 0 1rem;
		grid-template-columns: repeat(2, 1fr);
	}
	form {
		height: 7rem;
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		align-items: center;
	}
}
@media only screen and (max-width: 517px) {
	body {
		font-size: 12px;
	}
	section {
		padding: 0 1rem;
		margin-top: 1rem;
		margin-bottom: 2rem;
	}
	.containerBox {
		padding: 0 1rem;
		grid-template-columns: 1fr;
	}
	form input {
		width: 15rem;
	}
	form {
		height: 5.8rem;
	}
}
</style>
