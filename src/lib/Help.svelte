<svelte:options tag="sx-help" />

<script>
	import { Markdown } from './';

	export let src;
	export let visible;

	let button;
	let mask;
	let content;

	export function toggle() {
		visible = !visible;
	}
</script>

{#if visible}
	<div bind:this={mask} class:mask on:click={toggle}>
		<div bind:this={content} class:content class="markdown-body" on:click|stopPropagation>
			<Markdown {src}/>
		</div>
	</div>
{/if}

<!--button bind:this={button} class:button class="material-icons-outlined" on:click={toggle}>
	{#if visible}
		&#xE14C;
	{:else}
		&#xE88E;
	{/if}
</button-->
<a bind:this={button} class:button href="#" on:click={toggle}>Help</a>

<style>
	/*@import url('https://fonts.googleapis.com/icon?family=Material+Icons+Outlined');*/
	@import url('https://unpkg.com/github-markdown-css@4.0.0/github-markdown.css');

	.button {
		position: fixed;
		top: 0;
		right: 0;
		margin-top: 1rem;
		margin-right: 1rem;
	}

	.mask {
		background: rgba(0, 0, 0, 0.5);
	}

	.mask {
		position: fixed;
		inset: 0;
		display: flex;
		justify-content: center;
		align-items: center;
	}

	.content {
		max-width: 75%;
		max-height: 75%;
		padding: 1rem;
		overflow: scroll;
	}

	.content {
		background: white;
	}
</style>
