<script>
	import EmojiDisplay from './emojiDisplay.svelte'
	import EmojiDescription from './emojiDescription.svelte'
	import Button from './Button.svelte';
	import {fade, fly} from 'svelte/transition'

	let isLoaded = false;

	let currentEmoji = '\u{1F608}'
	const emojis = ['\u{1F923}', '\u{1F412}', '\u{1F680}']
	let m = {x:0, y:0}

	function randomizeEmoji(){
		return emojis[Math.floor(Math.random() * emojis.length)]
	}

	function handleRandomButton(){
		currentEmoji =  randomizeEmoji()
	}

	setTimeout(function(){
		isLoaded = true
	},2000)

	function handleMouseMove(event){
		m.x = event.clientX;
		m.y = event.clientY;
	}
</script>

<style>

</style>

<svelte:head>
	<link rel="stylesheet" href="/terminal.min.css">
</svelte:head>

<div class="container" on:mousemove={handleMouseMove}>
	<p>
		Position of mouse.: {m.x} x {m.y}
	</p>
	<h1>Randomize Emoji</h1>
	<ul>
		{#each emojis as  emo}
		<li>{emo}</li>
		{/each}
	</ul>
	{#if isLoaded === true}
	<div in:fly={{y: 200, duration: 2000}} out:fade>
		<EmojiDisplay {currentEmoji}/>
		<EmojiDescription/>
		<Button on:click|once={handleRandomButton} title={'\u{1F501} Randomize'}/>
	</div>
	{:else}
	<h2>Loading...</h2>
	{/if}
	<Button on:click={() => isLoaded = !isLoaded} title={"Toggle"} />
</div>
