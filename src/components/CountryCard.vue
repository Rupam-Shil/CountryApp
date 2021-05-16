<template>
	<router-link :to="'/country/' + country.alpha2Code">
		<div class="container__Box">
			<img class="imgBox" :src="countryFlag" alt="" />
			<div class="contentBox">
				<h4 class="countryName">{{ countryName }}</h4>
				<p>
					Population: <span>{{ countryPop }}</span>
				</p>
				<p>
					Region: <span>{{ countryRegion }}</span>
				</p>
				<p>
					Capital: <span>{{ countryCapital }}</span>
				</p>
			</div>
		</div>
	</router-link>
</template>

<script>
export default {
	props: ['country'],
	data() {
		return {
			countryFlag: this.country.flag,
			countryName: this.country.name,
			countryPop: this.country.population,
			countryRegion: this.country.region,
			countryCapital: this.country.capital,
		};
	},
};
</script>

<style scoped>
.container__Box {
	width: 15rem;
	height: 18rem;
	border-radius: 0.5rem;
	box-shadow: 0px 7px 7px 0px rgba(201, 201, 201, 0.75);
	-webkit-box-shadow: 0px 7px 7px 0px rgba(201, 201, 201, 0.75);
	-moz-box-shadow: 0px 7px 7px 0px rgba(201, 201, 201, 0.75);
}

.contentBox {
	margin-top: 1rem;
	padding: 0 2rem;
}
a:-webkit-any-link {
	text-decoration: none;
	color: #333;
}

.imgBox {
	height: 8rem;
	width: 100%;
	border-top-left-radius: 0.5rem;
	border-top-right-radius: 0.5rem;
}
.countryName {
	margin-bottom: 1rem;
}
p {
	font-size: 0.8rem;
	font-weight: 600;
}
p span {
	font-weight: 300;
}
</style>
