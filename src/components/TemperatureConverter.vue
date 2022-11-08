<template>
	<section class="Temperature">
		Celcius to Farenheit
		<input class="TemperatureConverter__input" type="number" placeholder="℃" v-model="valueCelcius"/>
		<div class="TemperatureConverter__output">{{ valueFarenheit }}F</div>
	</section>
</template>

<script>
export default {
	data() {
		return {
			valueCelcius: 0,
		}
	},

	computed: {
		valueFarenheit() {
			return (this.valueCelcius * 1.8) + 32;
		}
	}
}
</script>

<style>

.Temperature {
	position: absolute;
	margin: 10px;
	display: flex;
	flex-flow: column nowrap;
	top: 20.3em;
	left: 65%;
	width: 20em;
	padding: 2em;
	height: 11em;
	border-radius: 20px;
	background: #464646;
	font-family: "Days One";
	border: solid 2px black;
	box-shadow: 10px 15px 4px rgba(0, 0, 0, 0.3);
	color: white;
}

.TemperatureConverter__input {
	background: #6fb2ff90;
	border-radius: 10px;
	padding: 10px;
	margin: 5px;
	font-family: "ZCOOL QingKe HuangYou";
	font-size: 2em;
	border: solid 2px black;
}

</style>