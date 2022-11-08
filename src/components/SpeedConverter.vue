<template>
	<section class="SpeedConverter">
		MPH to KPH
		<input class="SpeedConverter__input" type="number" placeholder="MPH" v-model="valueMPH"/>
		<div class="SpeedConverter__output">{{ valueKPH }}KPH</div>
	</section>
</template>
	
<script>
	
export default {
	data() {
		return {
			valueMPH: 0,
		}
	},
	
	computed: {
		valueKPH() {
			return (this.valueMPH * 1.609344);
		}
	}
}
	
</script>
	
<style>

.SpeedConverter {
	position: absolute;
	margin: 10px;
	display: flex;
	flex-flow: column nowrap;
	top: 46em;
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
	
.SpeedConverter__input {
	background: #6fb2ff90;
	border-radius: 10px;
	padding: 10px;
	margin: 5px;
	font-family: "ZCOOL QingKe HuangYou";
	font-size: 2em;
	border: solid 2px black;
}

</style>