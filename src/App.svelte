<script>
		import { onMount } from 'svelte';

	var state = 0;
	function upstate(){
		state += 1
		localStorage.setItem("n", state);

	}
	function downstate() {
		state -=1
				localStorage.setItem("n", state);

	}
	function ups3() {
		state +=3
				localStorage.setItem("n", state);

	}
	function ds3() {
		state-=3
				localStorage.setItem("n", state);

	}
	function clear(){
		state = 0;
						localStorage.setItem("n", state);

	}
	onMount(async () => {
			if (typeof(Storage) !== "undefined") {
state = parseInt(localStorage.getItem("n")) || 0
} else {
alert(`ERROR! Refresh the page, and if it continues, call K_TECH 
error code:LOCALSTORAGE_NULL_OR_UNDEFINED `)
				while (true){}
}


	});

</script>

<style>
	button{
		width: 90px;
		height: 70px;
		
	}
</style>

<main>
	<h3>{state}</h3>
<button on:click={upstate}>+1</button>
	<button on:click={ups3}>+3</button>

<button on:click={downstate}>-1</button>
	<button on:click={ds3}>-3</button>


	<button on:click={clear}>reset</button>


</main>
