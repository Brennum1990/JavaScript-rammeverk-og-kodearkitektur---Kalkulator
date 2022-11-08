<template>
	
	<div class="calculator">
		<div class="screen">
			<div class="screen__numbers">{{ showingResult ? currentResult : currentInput }}</div>
		</div>
		
		<div class="buttons">
		<span>
			<button @click="clearResult" class="button__grey">C</button>
			<button class="button__grey">+/-</button>
			<button class="button__grey">%</button>
			<button @click="handleOperatorInput('/')" class="button__yellow">÷</button>
		</span>
		<span>
			<button @click="handleInput(1)" class="button__beige">1</button>
			<button @click="handleInput(2)" class="button__beige">2</button>
			<button @click="handleInput(3)" class="button__beige">3</button>
			<button @click="handleOperatorInput('*')" class="button__yellow">x</button>
		</span>
		<span>
			<button @click="handleInput(4)" class="button__beige">4</button>
			<button @click="handleInput(5)" class="button__beige">5</button>
			<button @click="handleInput(6)" class="button__beige">6</button>
			<button @click="handleOperatorInput('-')" class="button__yellow">-</button>
		</span>
		<span>
			<button @click="handleInput(7)" class="button__beige">7</button>
			<button @click="handleInput(8)" class="button__beige">8</button>
			<button @click="handleInput(9)" class="button__beige">9</button>
			<button @click="handleOperatorInput('+')" class="button__yellow">+</button>
		</span>
		<span>
			<button @click="handleInput(0)" class="button__0">0</button>
			<button @click="handleInput('.')" class="button__beige">.</button>
			<button @click="handleEqualsInput" class="button__yellow">=</button>
		</span>
		</div>
	</div>

	<div class="calculator-info">
			<div>currentResult: {{ currentResult }}</div>
			<div>currentInput: {{ `"${currentInput}"` || `""` }}</div>
			<div>currentInputAsNumber: {{ currentInputAsNumber }}</div>
			<div>currentOperator: {{ currentOperator || `""` }}</div>
		</div>
		
</template>

<script>
	export default {
		data() {
			return {
				currentResult: 0,
				currentInput: '',
				currentOperator: null,
				showingResult: false,
			}
		},

		created() {
			window.addEventListener('keyup', this.handleKeyup);
		},
		
		computed: {
			currentInputAsNumber() {
				return Number(this.currentInput)
			},
		},

		methods: {
			calculateResult() {
				switch(this.currentOperator) {
					case '+':
						this.currentResult += this.currentInputAsNumber;
						break;
					case '-':
						this.currentResult -= this.currentInputAsNumber;
						break;
					case '/':
						this.currentResult /= this.currentInputAsNumber;
						break;
					case '*':
						this.currentResult *= this.currentInputAsNumber;
						break;
					default:
						this.currentResult = this.currentInputAsNumber;
				}
			},

			clearResult() {
				this.currentResult = 0;
				this.currentInput = '';
				this.currentOperator = null;
				this.showingResult = false;
			},
			
			handleOperatorInput(operator) {
				this.calculateResult();
				this.currentOperator = operator;
				this.currentInput = '';
				this.showingResult = true;
			},

			handleInput(digit) {
				this.currentInput += digit;
				this.showingResult = false;
			},
			
			handleEqualsInput() {
				this.calculateResult();
				this.showingResult = true;
			},

			handleKeyup(event) {
				switch(event.key) {
					case '0':
					case '1':
					case '2':
					case '3':
					case '4':
					case '5':
					case '6':
					case '7':
					case '8':
					case '9':
						this.handleInput(event.key)
						break;
					case '+':
					case '-':
					case '/':
					case '*':
						this.handleOperatorInput(event.key)
						break;
					case '.':
					case ',':
						this.handleInput('.')
						break;
					case '=':
					case 'Enter':
						this.handleEqualsInput()
						break;
					case 'Escape':
					case 'Backspace':
						this.clearResult()
						break;
				}
			}
		}
	}
	
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=ZCOOL+QingKe+HuangYou&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Days+One&display=swap');

* {
	box-sizing: border-box;
	padding: 0;
	margin: 0;
}
button { 
	cursor: pointer;
	border-radius: 20px;
	width: 95px;
	height: 95px;
	font-family: 'Days One';
	font-size: 30px;
}

button:hover { 
	transform: scale(1.02);
}

body {
	background-color: rgb(187, 202, 207);
}

.calculator {
	width: 563px;
	height: 792px;
	position: absolute;
	top: 50%;
	left: 35%;
	transform: translate(-50%, -50%);
	background-color: #464646; 
	display: flex;
	flex-flow: column nowrap;
	border-radius: 15px;
	border: 2px solid black;
	box-shadow: 10px 15px 4px rgba(0, 0, 0, 0.3);
	padding-top: 30px;
}

.screen {
	width: 503px;
	height: 158px;
	border: 2px solid black;
	border-radius: 15px;
	margin: auto;
}

.screen__numbers {
	background: #6fb2ff90;
	font-family: 'ZCOOL QingKe HuangYou';
	width: 499px;
	height: 154px;
	border-radius: 14px;
	font-size: 115px;
	color: white;
	text-align: right;
	padding-right: 5px;
	padding-top: 30px;
	overflow: hidden;
}

.buttons { 
 	margin: auto;
	display: flex;
	flex-flow: column nowrap;
	padding-bottom: 20px;
}

.buttons button {
	margin: 5px;
}

.button__beige {
	background-color: #FFFEE4;
}

.button__grey {
	background-color: #CFCFCF;
}

.button__yellow {
	background-color: #FFE663;
}

.button__0 {
	background-color: #FFFEE4;
	width: 200px;
	height: 95px;
	border-radius: 20px;
}

.calculator-info { 
	font-family: 'Crete Round';
	font-size: 20px;
	left: 35%;
	position: absolute;
	top: 7%;
	left: 35%;
	transform: translate(-50%, -50%);
	text-align: center;
	font-family: 'Days One';
	z-index: -1;
}
</style>