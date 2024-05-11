<script setup>
	import { ref } from 'vue';
	import jsonData from '../data/data.json';

	//data section
	let flightOffer = ref([]);
	flightOffer = jsonData.flightOffer?.map((flightOffer) => {
		const updatedItineraries = flightOffer.itineraries?.map((itinerary) => {
			const updatedSegments = itinerary.segments?.map((segment) => {
				return {
					...segment,
					duration: itinerary.duration,
					price: flightOffer.price,
					fareBasis: flightOffer.fareBasis,
					class: flightOffer.class,
					seat: flightOffer.seat
				};
			});
			return {
				...itinerary,
				segments: updatedSegments
			};
		});
		return {
			...flightOffer,
			itineraries: updatedItineraries
		};
	});

	console.log(flightOffer);
</script>

<template>
	<section class="py-8">
		<table class="w-full border-collapse">
			<thead class="flex-grow">
				<tr class="bg-gray-200 h-10 text-gray-500 text-xs tracking-wider">
					<th class="w-[20%] text-start px-2 uppercase">Flight</th>
					<th class="w-[12%] text-start px-2 uppercase">Aircraft</th>
					<th class="w-[10%] text-center px-2 uppercase">Class</th>
					<th class="w-[10%] text-center px-2 uppercase">Fare</th>
					<th class="w-[10%] text-center px-2 uppercase">Route</th>
					<th class="w-[8%] text-center px-2 uppercase">Departure</th>
					<th class="w-[10%] text-center px-2 uppercase">Arrival</th>
					<th class="w-[10%] text-center px-2 uppercase">Duration</th>
					<th class="w-[10%] text-end px-2 uppercase">Price</th>
				</tr>
			</thead>
			<template v-for="(flight, flightIndex) in flightOffer" :key="flightIndex">
				<tbody class="flex-grow">
					<tr
						class="py-4"
						v-for="(flightItem, itemIndex) in flight.itineraries[0]?.segments"
						:key="itemIndex"
						:class="{
							'border-b-2 border-red-700': itemIndex + 1 == flight.itineraries[0]?.segments?.length
						}">
						<td class="w-[20%] text-start px-2 text-gray-500 text-xs">
							<p>{{ flightItem.aircraft || '' }}</p>
						</td>
						<td class="w-[12%] text-start px-2 text-gray-500 text-xs">Malcolm Lockyer</td>
						<td class="w-[10%] text-center px-2 text-gray-500 text-xs">1961</td>
						<td class="w-[10%] text-center px-2 text-gray-500 text-xs">1961</td>
						<td class="w-[10%] text-center px-2 text-gray-500 text-xs">1961</td>
						<td class="w-[8%] text-center px-2 text-gray-500 text-xs">1961</td>
						<td class="w-[10%] text-center px-2 text-gray-500 text-xs">1961</td>
						<td class="w-[10%] text-center px-2 text-gray-500 text-xs">1961</td>
						<td class="w-[10%] text-end px-2 text-gray-500 text-xs">
							<div>
								<p>12222</p>
								<button
									v-if="itemIndex + 1 == flight.itineraries[0]?.segments?.length"
									class="bg-blue-800 px-3 py-0.5 rounded-sm text-white tracking-wider hover:bg-blue-500 transition-all">
									Search
								</button>
							</div>
						</td>
					</tr>
				</tbody>
			</template>
		</table>
	</section>
</template>
