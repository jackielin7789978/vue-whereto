<script setup lang="ts">
import { ref, computed } from 'vue'
import { TAIWAN_AREA } from './constants'
import { getRandomArrayItem } from './utils'

const targetCity = ref('')
const targetDist = computed(() => {
	return getRandomArrayItem(TAIWAN_AREA[targetCity.value])
})

const getRandomCity = () => {
	const cities = Object.keys(TAIWAN_AREA)
	targetCity.value = getRandomArrayItem(cities)
}
getRandomCity()
</script>
<template>
	<div class="select-none flex items-center gap-x-4 lg:gap-x-8">
		<div class="w-54 lg:w-58">
			我想到 {{ targetCity }} {{ targetDist }} 去玩玩
		</div>
		<button
			@click="getRandomCity"
			class="cursor-pointer px-4 py-1 rounded hover-transition bg-[#24436D] hover:(bg-[#192E4B] text-light-900) active:(bg-[#15263F])"
		>
			GO
		</button>
	</div>
</template>

<style lang="scss">
#app {
	min-height: 100%;
	background: #1d3557;
	color: #fff;
	font-family: 'Noto Sans TC', sans-serif;
	font-weight: normal;
	position: relative;
	display: flex;
	align-items: center;
	justify-content: center;
}

.hover-transition {
	@apply transition-all 0.5s ease;
}
</style>
