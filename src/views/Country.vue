<template>
	<section class="eachCountry">
		<router-link to="/" class="back-btn"
			><i class="uil uil-arrow-left back__icon"></i>Back</router-link
		>
		<main>
			<div class="left__col">
				<img class="eachFlag" :src="eachFlag" alt="" />
			</div>
			<div class="right__col">
				<h1 class="c__name">{{ countryDetails.name }}</h1>
				<div class="inner-container">
					<div class="inner__left">
						<p class="innerContent" v-if="countryDetails.nativeName">
							Native Name:
							<span class="innerDetails">{{ countryDetails.nativeName }}</span>
						</p>
						<p class="innerContent">
							Population:
							<span class="innerDetails">{{ countryDetails.population }}</span>
						</p>
						<p class="innerContent">
							Region:
							<span class="innerDetails">{{ countryDetails.region }}</span>
						</p>
						<p class="innerContent" v-if="countryDetails.subregion">
							Sub Region:
							<span class="innerDetails">{{ countryDetails.subregion }}</span>
						</p>
						<p class="innerContent" v-if="countryDetails.capital">
							Capital:
							<span class="innerDetails">{{ countryDetails.capital }}</span>
						</p>
					</div>
					<div class="inner__right">
						<p class="innerContent">
							Area:
							<span class="innerDetails">{{ countryDetails.area }} km²</span>
						</p>
						<p class="innerContent">
							Currencies:
							<span class="innerDetails">{{ currencies }}</span>
						</p>
						<p class="innerContent">
							Languages:
							<span class="innerDetails">{{ languages }}</span>
						</p>
					</div>
				</div>
				<div class="border" v-if="borders.length > 0">
					<h4>
						Border Countries:
						<div class="borderBox" v-for="(border, i) in borders" :key="i">
							{{ border }}
						</div>
					</h4>
				</div>
			</div>
		</main>
	</section>
</template>
<script>
export default {
	data() {
		return {
			countryDetails: {},
			eachFlag: '',
			languages: '',
			currencies: '',
			borders: [],
		};
	},
	async created() {
		await fetch(
			`https://restcountries.eu/rest/v2/alpha/${this.$route.params.id}`
		)
			.then((res) => res.json())
			.then((data) => {
				this.countryDetails = data;
				this.eachFlag = this.countryDetails.flag;
				const temp = [];
				this.countryDetails.languages.forEach((lang) => {
					temp.push(lang.name);
				});
				this.languages = temp.toString();
				this.currencies = this.countryDetails.currencies[0].name;
				this.borders = this.countryDetails.borders;
			});
	},
};
</script>
<style>
*,
*::before,
*::after {
	margin: 0;
	padding: 0;
}
.eachCountry {
	padding: 4rem;
	width: 100vw;
	height: calc(100vh - 4rem);
	margin: 0;
}
.back-btn {
	display: block;
	background-color: #fff;
	width: 8rem;
	padding: 0.4rem 1.6rem;
	text-decoration: none;
	border-radius: 0.2rem;
	box-shadow: 3px 3px 10px rgba(0, 0, 0, 0.2);
	transition: 0.3s;
	margin-bottom: 4rem;
	color: #333;
}
.back__icon {
	font-size: 1.2em;
	margin-right: 1rem;
}
.back-btn:hover {
	background: rgb(255, 250, 250);
	box-shadow: 0px 5px 10px rgba(0, 0, 0, 0.2);
}
main {
	height: 25rem;
	width: 100%;
	display: flex;
	justify-content: space-between;
	align-items: center;
}
.left__col {
	width: 50%;
	height: 100%;
	margin-right: 5rem;
}
.left__col img {
	height: 100%;
	width: 100%;
}
.right__col {
	width: 50%;
	height: 100%;
	padding: 2rem 0;
}
.right__col .c__name {
	margin-bottom: 1.8rem;
	font-weight: 600;
}
.inner-container {
	display: grid;
	grid-template-columns: repeat(2, 1fr);
	margin-bottom: 4rem;
}
.inner__left,
.inner__right {
	line-height: 2rem;
}
.innerContent {
	font-weight: 500;
}
.innerDetails {
	font-weight: 200;
}
h4 {
	display: inline-block;
}
.borderBox {
	font-weight: 200;
	display: inline-block;
	border: 1px solid #333;
	border-radius: 0.2rem;
	padding: 0.2rem 0.5rem;
	margin-right: 1rem;
}
@media only screen and (max-width: 968px) {
	.eachCountry {
		padding: 2rem;
	}
	main {
		height: 20rem;
		align-items: unset;
	}
	.inner-container {
		margin-bottom: 2rem;
	}
	h4 {
		display: unset;
	}
	.right__col {
		padding: unset;
	}
}
@media only screen and (max-width: 816px) {
	main {
		height: unset;
		width: 100%;
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		align-items: center;
	}
	.back-btn {
		margin-bottom: 2rem;
	}
}
@media only screen and (max-width: 517px) {
	.inner-container {
		display: grid;
		grid-template-columns: auto;
	}
	.right__col .c__name {
		margin-bottom: 1rem;
	}
}
</style>
