<template>
	<Calculator/>
	<WeightConverter/>
	<TemperatureConverter/>
	<LengthConverter/>
	<SpeedConverter/>
</template>

<script>
	import Calculator from '../components/Calculator.vue'
	import WeightConverter from '../components/WeightConverter.vue'
	import TemperatureConverter from '../components/TemperatureConverter.vue'
	import LengthConverter from '../components/LengthConverter.vue'
	import SpeedConverter from '../components/SpeedConverter.vue'


	export default {
		components: {
			Calculator,
			WeightConverter,
			TemperatureConverter,
			LengthConverter,
			SpeedConverter
		}
	}
</script>

<style>
	/* @import 'style.css'; */
</style>