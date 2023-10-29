<script>
  import Records from './records.json';
  import {
    onMount,
  } from 'svelte';
  import Tag from '$lib/controls/tag/Tag.svelte';
	import { text } from '@sveltejs/kit';

  /**
   * @type {Array<object>}
   */
  let posts = [];

  onMount(() => {
    console.log(Records);

    posts = Records;
  });
</script>

<style>
  article {
    display: flex;
    flex-direction: column;
    row-gap: 1rem;

    & > .post {
      display: grid;
      grid-template-columns: 1fr;
      grid-template-rows: repeat(3, auto);
      row-gap: 1rem;
      padding: 0.5rem;
      
      background-color: var(--theme-darker_white);

      & > .tag-list {
        display: flex;
        column-gap: 0.5rem;
      }
    }
  }
</style>

<article>
  {#each posts as post}
    <div class="post" href="{post.href}">
      <h2>{post.title}</h2> 
      <div class="tag-list">
        {#each post.tags as tag}
          <Tag text={tag} value={tag} />
        {/each}
      </div>
      <div class="abstract">{post.abstract}</div>
      <a class="href" href="{post.href}">{post.href}</a>
    </div>
  {/each}
</article>