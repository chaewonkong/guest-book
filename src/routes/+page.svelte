<script lang="ts">
	import Post from "$lib/post.svelte";
import { get, writable } from "svelte/store";

	interface Post {
		visitor: string;
		content: string;
	}

	let visitor = '';
	let content = '';
	let posts: Post[] = []

	function handleSubmit(e: SubmitEvent) {
		if (visitor.length && content.length) {
			posts = [...posts, {visitor, content}]
		}
		visitor = ""
		content = ""
	}
</script>

<h1>Guest Book</h1>
<div>
	<form on:submit|preventDefault={handleSubmit}>
		<div style:display="flex" style:flex-direction="column" style:max-width="600px">
			<input placeholder="작성자명" bind:value={visitor} />
			<textarea placeholder="방명록을 작성하세요" bind:value={content} />
			<button>submit</button>
		</div>
	</form>
</div>
{#each posts as post}
<Post visitor={post.visitor} content={post.content} />
{/each}
