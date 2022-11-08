<template>
	<section class="lengthConverter">
		Feet to Cm
		<input class="lengthConverter__input" type="number" placeholder="ft" v-model="valueFeet"/>
		<div class="lengthConverter__output">{{ valueCm }}CM</div>
	</section>
</template>

<script>
export default {
	data() {
		return {
			valueFeet: 0,
		}
	},

	computed: {
		valueCm() {
			return (this.valueFeet * 30.48);
		}
	}
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=ZCOOL+QingKe+HuangYou&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Days+One&display=swap');

.lengthConverter {
	position: absolute;
	margin: 10px;
	display: flex;
	flex-flow: column nowrap;
	top: 7.4em;
	left: 65%;
	width: 20em;
	height: 11em;
	padding: 2em;
	gap: .5em;
	border-radius: 20px;
	border: solid 2px black;
	background: #464646;
	font-family: "Days One";
	color: white;
	box-shadow: 10px 15px 4px rgba(0, 0, 0, 0.3);
}

.lengthConverter__input {
	background: #6fb2ff90;
	border-radius: 10px;
	padding: 10px;
	font-family: "ZCOOL QingKe HuangYou";
	border: solid 2px black;
	font-size: 2em;
}

input {
	border: 0;
	color: inherit;
}

</style>