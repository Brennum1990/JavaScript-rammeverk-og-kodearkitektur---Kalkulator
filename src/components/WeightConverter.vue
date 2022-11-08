<template>
<section class="WeightConverter">
			Pounds to Kilo
			<input class="WeightConverter__input" type="number" placeholder="lbs" v-model="valuePound"/>
			<div class="WeightConverter__output">{{ valueKilo }}Kg</div>
		</section>
</template>

<script>

export default {
	data() {
		return {
			valuePound: 0,
		}
	},

	computed: {
		valueKilo() {
			return (this.valuePound * 0.453);
		}
	}
}

</script>

<style>
.WeightConverter {
	position: absolute;
	margin: 10px;
	display: flex;
	flex-flow: column nowrap;
	top: 33.2em;
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

.WeightConverter__input {
	background: #6fb2ff90;
	border-radius: 10px;
	padding: 10px;
	margin: 5px;
	font-family: "ZCOOL QingKe HuangYou";
	font-size: 2em;
	border: solid 2px black;
}

</style>

