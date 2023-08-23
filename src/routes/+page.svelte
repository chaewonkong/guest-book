<script lang="ts">
	let visitor = '';
	let content = '';
	function handleSubmit(e: SubmitEvent) {
		if (visitor.length && content.length) {
			alert(`${visitor}: ${content}`);
		}
	}
</script>

<h1>Welcome to SvelteKit</h1>
<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>
<div>
	<form on:submit|preventDefault={handleSubmit}>
		<div style:display="flex" style:flex-direction="column" style:max-width="600px">
			<input placeholder="작성자명" bind:value={visitor} />
			<textarea placeholder="방명록을 작성하세요" bind:value={content} />
			<button>submit</button>
		</div>
	</form>
</div>
