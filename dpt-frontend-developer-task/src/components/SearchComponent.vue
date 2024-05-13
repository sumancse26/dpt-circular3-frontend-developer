<script setup>
	import { reactive, ref } from 'vue';
	const props = defineProps({
		getSearchObj: Function
	});
	const active = ref(true);
	const searchObj = reactive({
		LHR: null,
		CDG: null,
		date: null,
		searchActive: false
	});

	const searchBtnHandler = () => {
		searchObj.searchActive = true;
		props.getSearchObj(searchObj);
	};
</script>

<template>
	<section class="border-t-2 border-solid border-slate-400">
		<!-- tab section -->
		<div class="tab flex justify-center py-2">
			<ul class="flex items-center border-2 border-solid border-[#abaeb4] rounded text-sm">
				<li class="py-1 px-2">
					<p>Round Trip</p>
				</li>
				<li
					class="py-1 px-2 border-2 border-b-0 border-t-0 border-solid border-[#abaeb4]"
					:class="{ 'bg-blue-800': active }">
					<p class="text-white">One Way</p>
				</li>
				<li class="py-1 px-2">
					<p>Multi City</p>
				</li>
			</ul>
		</div>

		<!-- input section -->

		<div class="flex justify-between items-center gap-4 border-t-2 border-b-2 py-4">
			<div class="flex gap-4">
				<input
					v-model.trim="searchObj.LHR"
					type="text"
					placeholder="LHR"
					class="outline outline-2 outline-[#abaeb4] outline-offset-2 rounded-sm px-2 focus:outline-blue-800" />
				<input
					v-model.trim="searchObj.CDG"
					type="text"
					placeholder="CDG"
					class="outline outline-2 outline-[#abaeb4] outline-offset-2 rounded-sm px-2 focus:outline-blue-800" />
				<input
					v-model.trim="searchObj.date"
					type="date"
					class="outline outline-2 outline-[#abaeb4] outline-offset-2 rounded-sm px-2 focus:outline-blue-800" />
			</div>

			<div class="flex gap-4">
				<select
					class="outline outline-2 outline-[#abaeb4] outline-offset-2 rounded-sm px-3 focus:outline-blue-800">
					<option>Day-</option>
					<option>option 1</option>
					<option>option 2</option>
				</select>
				<select
					class="outline outline-2 outline-[#abaeb4] outline-offset-2 rounded-sm px-3 focus:outline-blue-800">
					<option>Day+</option>
					<option>option 1</option>
					<option>option 2</option>
				</select>
				<select
					class="outline outline-2 outline-[#abaeb4] outline-offset-2 rounded-sm px-3 focus:outline-blue-800">
					<option>Any time</option>
					<option>option 1</option>
					<option>option 2</option>
				</select>
			</div>

			<div class="flex gap-4">
				<span>+</span>
				<select
					class="outline outline-2 outline-[#abaeb4] outline-offset-2 rounded-sm px-3 focus:outline-blue-800">
					<option>ADT</option>
					<option>option 1</option>
					<option>option 2</option>
				</select>
				<select
					class="outline outline-2 outline-[#abaeb4] outline-offset-2 rounded-sm px-3 focus:outline-blue-800">
					<option>1</option>
					<option>2</option>
					<option>3</option>
				</select>
				<span>+</span>
			</div>
		</div>
		<div class="flex gap-4 justify-between border-b-2 py-2">
			<span class="flex items-center">
				<input type="checkbox" id="extra-options" class="mt-[2px]" name="Extra Options" value="Extra Options" />
				<label for="extra-options" class="pl-1">Extra Options</label>
			</span>
			<form>
				<div class="flex items-center gap-4">
					<span>Environment</span>
					<div class="flex gap-2">
						<span class="flex items-center">
							<input id="dummy" type="radio" class="mr-1 -mb-1" name="input-radio" placeholder="dummy" />
							<label for="dummy">Dummy</label>
						</span>
						<span>
							<input id="pdt" type="radio" class="mr-1 -mb-2" name="input-radio" placeholder="PDT" />
							<label for="pdt">PDT</label>
						</span>
					</div>
				</div>
			</form>
			<button
				@click="searchBtnHandler"
				class="bg-blue-800 px-3 py-0.5 rounded-sm text-white tracking-wider hover:bg-blue-500 transition-all">
				Search
			</button>
		</div>
		<span>Data parsed successfully</span>
	</section>
</template>
