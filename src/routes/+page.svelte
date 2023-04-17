<title>Calculator</title>
<body>
	
</body>
<script>
// @ts-nocheck

	let total = 0;
	let console = "";
	/**
	 * @type {string | null}
	 */
	let number = null;
	function resolveState(){
		switch(number){
			case "add":
				total += parseFloat(console);
				console = "0";
				break;
			case "substract":
				total -= parseFloat(console);
				console = "0";
				break;
			case "multiply":
				total *= parseFloat(console);
				console = "0";
				break;
			case "divide":
				total /= parseFloat(console);
				console = "0";
				break;
			default:
				total = parseFloat(console);
				console = "0";
				break;
		}
	}
	/**
	 * @param {string} operation
	 */
	function setOperation(operation){
		resolveState();
		number = operation;
	}
	/**
	 * @param {string | number} value
	 */
	function setValue(value){
		if(console.toString() == "0" || number == "equal"){
			console = "";
		}
		if(number == "equal"){
			number = null;
		}
		if(value == "C"){
			total = 0;
			number = null;
			console = "";
			return;
		}
		console = console + value;
	}
	function equal(){
		resolveState();
		// @ts-ignore
		console = total;
		number = "equal";
	}
</script>

<style>
	body{
		background-color: RGB(68, 184, 172);
	}
	.calculator {
		position:absolute;
		top:50%;
		left:50%;
		transform:translate(-50%,-50%);
		width:300px;
		border:1px solid #975959;
		box-shadow:2px 2px 2px RGB(152, 180, 212);
		padding:10px;
        background-color: RGB(0, 155, 119);
        height: 180px;
	}
	.calculator input {
		width:85.5%;
		padding:20px;
		outline:none;
		text-align:right;
		font-size:20px;
        background-color: #a3bcc5;
	}
	.calculator .buttons {
		display: flex;
		flex-wrap:wrap;
	}
	.calculator .buttons .operations {
		display:flex;
		justify-content:space-between;
		width:100%;
	}
	.calculator .buttons .operations button {
		width:25%;
	}
	.calculator .buttons .numbers {
		width:78%;
	}
	.calculator .buttons .numbers > div {
		display:flex;
	}
	.calculator .buttons .numbers > div button {
		width:32%;
	}
	.calculator .equal {
		flex: auto;
	}
	.calculator .equal button {
		width:100%;
		height:100%;
		background:#a3bcc5;
		color:#eee;
	}
	.calculator button {
		outline:none;
        background-color: white;
	}
</style>

<div class="calculator">
	<input type="text" bind:value={console} readonly="true"/>
	<div class="buttons">
		<div class="operations">
			<button on:click={()=>{setOperation('add');}}>
				+
			</button>
			<button on:click={()=>{setOperation('substract');}}>
				-
			</button>
			<button on:click={()=>{setOperation('multiply');}}>
				&times;
			</button>
			<button on:click={()=>{setOperation('divide');}}>
				&divide;
			</button>
		</div>
		<div class="numbers">
			<div>
				<button on:click={()=>{setValue(7);}}>
					7
				</button>
				<button on:click={()=>{setValue(8);}}>
					8
				</button>
				<button on:click={()=>{setValue(9);}}>
					9
				</button>
			</div>
			<div>
				<button on:click={()=>{setValue(4);}}>
					4
				</button>
				<button on:click={()=>{setValue(5);}}>
					5
				</button>
				<button on:click={()=>{setValue(6);}}>
					6
				</button>
			</div>
			<div>
				<button on:click={()=>{setValue(1);}}>
					1
				</button>
				<button on:click={()=>{setValue(2);}}>
					2
				</button>
				<button on:click={()=>{setValue(3);}}>
					3
				</button>
			</div>
			<div>
				<button on:click={()=>{setValue(0);}}>
					0
				</button>
				<button on:click={()=>{setValue('.');}}>
					.
				</button>
				<button on:click={()=>{setValue('C');}}>
					C
				</button>
			</div>
		</div>
		<div class="equal">
			<button on:click={equal}>
				=
			</button>
		</div>
	</div>
</div>
