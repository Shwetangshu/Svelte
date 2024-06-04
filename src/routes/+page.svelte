<script lang="ts">
	import { formatDate } from '$lib/utils'
	import * as config from '$lib/config'

	export let data
</script>

<svelte:head>
	<title>{config.title}</title>
</svelte:head>

<!-- <section>
	<ul class="posts">
		{#each data.posts as post}
			<li class="post">
				<a href={post.slug} class="title">{post.title}</a>
				<p class="date">{formatDate(post.date)}</p>
				<p class="description">{post.description}</p>
			</li>
		{/each}
	</ul>
</section> -->
<div class="grid grid-cols-8 posts">
    <!-- Column 1 -->
    <div class="flex flex-col div1">
        {#each data.posts as post, index}
        {#if index % 1 === 0}
        <div class="flex flex-col">
            <a href={post.slug} class="title">{post.title}</a>
            <p class="date">{formatDate(post.date)}</p>
            <p class="description">{post.description}</p>
        </div>
        {/if}
        {/each}
    </div>
</div>



<style>
	 .posts {
		display: grid;
		gap: var(--size-7);
	}
/*
	.post {
		max-inline-size: var(--size-content-3);
	}

	.post:not(:last-child) {
		border-bottom: 1px solid var(--border);
		padding-bottom: var(--size-7);
	}
*/

	.title {
		font-size: var(--font-size-fluid-3);
		text-transform: capitalize;
	}

	.date {
		color: var(--text-2);
	}

	.description {
		margin-top: var(--size-3);
	} 


@media (prefers-color-scheme: dark) {
    .div1 {
        background-color: var(--bg-color-div1-dark);
    }
   
}

@media (prefers-color-scheme: light) {
    .div1 {
        background-color: var(--bg-color-div1-light);
    }
  
}
</style>