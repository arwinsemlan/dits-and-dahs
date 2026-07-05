<script>
	import { onMount } from 'svelte';
	import './layout.css';

	const { children } = $props();

	let word = $state('');

	onMount(async () => {
		const commonWords = await fetch('words.txt');
		let formatedWords = (await commonWords.text()).split('\n');
		word = formatedWords[Math.floor(Math.random() * formatedWords.length)];
	});
</script>

<h1>{word}</h1>

{@render children()}
