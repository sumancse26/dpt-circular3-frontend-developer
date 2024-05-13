<script setup>
	import { ref } from 'vue';
	import Flight from '../components/Flight.vue';
	import Navbar from '../components/Navbar.vue';
	import SearchComponent from '../components/SearchComponent.vue';

	let searchedData = ref({});
	const getFlightSearch = async (data) => {
		searchedData.value = await data;
	};
</script>

<template>
	<Navbar />
	<div class="mx-auto max-w-7xl px-2 sm:px-6 lg:px-8">
		<SearchComponent :getSearchObj="getFlightSearch" />
		<Flight :searchFlight="searchedData" />
	</div>
</template>
