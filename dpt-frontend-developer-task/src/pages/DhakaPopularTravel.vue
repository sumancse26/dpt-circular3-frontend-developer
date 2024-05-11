<script setup>
	import Flight from '../components/Flight.vue';
	import Navbar from '../components/Navbar.vue';
	import SearchComponent from '../components/SearchComponent.vue';
</script>

<template>
	<Navbar />
	<div class="mx-auto max-w-7xl px-2 sm:px-6 lg:px-8">
		<SearchComponent />
		<Flight />
	</div>
</template>
