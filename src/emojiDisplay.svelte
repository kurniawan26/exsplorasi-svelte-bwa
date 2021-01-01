<script>
    export let currentEmoji; 
    let current = 'button1';
</script>

<style>
	div{
        margin-bottom: 0.5em;
        font-size: 3em;
    }

</style>

<div>{currentEmoji}</div>
<button
 class="btn"
 class:btn-error={current === 'button1'}
 on:click={() => (current = 'button1')}>
 Button 1</button>

 <button 
 class="btn"
 class:btn-error={current === 'button2'}
 on:click={() => (current = 'button2')}>
 Button 2</button>

 <button 
 class="btn"
 class:btn-error={current === 'button3'}
 on:click={() => (current = 'button3')}>
 Button 3</button>