<script>
		import { onMount } from 'svelte';
var left = null
	var state = 0;
	var ifgoal = false
	var goal_v = 0
	window.isd = 1
	function upstate(){
		state += 1
		left = goal_v-state
		localStorage.setItem("n", state);

	}
	function downstate() {
		state -=1
		
				left = goal_v-state

				localStorage.setItem("n", state);

	}
function dark(){
if(window.isd==0)
{document.querySelector(":root").style.color = "white"
document.querySelector(":root").style.backgroundColor = "black"
window.isd = 1;

}
else if(window.isd==1){
document.querySelector(":root").style.color = "black"
document.querySelector(":root").style.backgroundColor = "white"
window.isd = 0;
}
}
	
	function setstate() {
		state = Number(prompt())
		localStorage.setItem("n", state);
		left = goal_v-state
	}
	function ups3() {
		state +=3
				left = goal_v-state

				localStorage.setItem("n", state);

	}
	function ds3() {
		state-=3
				left = goal_v-state

				localStorage.setItem("n", state);

	}
	function clear(){
		state = 0;
				left = goal_v-state

			localStorage.setItem("n", state);

	}
	function goal() {
		 goal_v = prompt()
		if (goal_v==0){
			ifgoal = false
		}
		else{
			ifgoal=true
		}
		left = goal_v-state
		localStorage.setItem("g", goal_v);
	}
	onMount(async () => {
			if (typeof(Storage) !== "undefined") {
state = parseInt(localStorage.getItem("n")) || 0
	goal_v = parseInt(localStorage.getItem("g"))||0
				if (goal_v !=0){ifgoal=1}
			left = goal_v-state

				console.log(goal_v)
} else {
alert(`ERROR! Refresh the page, and if it continues, call K_TECH 
error code:3701 `)
				while (true){}
}


	});

</script>

<style>
	:root{
		color:white; background-color: black;
	}
	button{
		width: 90px;
		height: 70px;
		
	}
	#footer {
    position: absolute;
    bottom: 30px;
    width: 100%;
}

</style>

<main>
	<h3>{state}</h3>
<button on:click={upstate}>+1</button>
	<button on:click={ups3}>+3</button>

<button on:click={downstate}>-1</button>
	<button on:click={ds3}>-3</button>
	<button on:click={clear}>reset</button>
		<button on:click={setstate}>set to</button>

	<br><br>	<br><br>
	<br><br>
	<br><br>
{#if ifgoal}
you have {left} left
	<br>
{/if}
<button on:click={goal}>set a goal</button>
<br>
<button on:click={dark}>toggle dark</button>


	<div id="footer">made by k-tech and butler math and science club</div>
</main>
