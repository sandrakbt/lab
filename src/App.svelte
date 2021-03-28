<script>
	import { onMount } from 'svelte';
	import Person from './Person.svelte';

	let people = [];

	onMount(async () => {
		people = await getPeople(2);
		console.log(people)
	});

	function getPeople(page) {
		return fetch(`https://www.swapi.tech/api/people?page=${page}&limit=10`)
			.then(res => res.json())
			.then(data => data.results)
	}
</script>

<main class="body">
	<h1><img src="Star_Wars_Logo.svg.png" width="350px"></h1>
	<p class="p">Characteristics of some characters from the movies:</p>
	{#each people as person, i}
		<Person url={person.url} />
	{/each}
</main>

<style>
.body {
	background-color: black;
}
.h1 {
	color: gold;
	font-size: xx-large;
	margin-top: 0px;
}
.p {
	color: white;
	font-size: x-large;
}
</style>