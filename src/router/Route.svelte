<script>
  export let path;
  
  import page from 'page';
  import { getContext, onMount } from 'svelte';
  const current_path = getContext('current_path');
  
  let id;
  onMount(() => {
    page(path, (ctx) => {
      $current_path = path;
      // console.log(ctx.params.id);
      id = ctx.params.id;
    });
  });
</script>

{#if path == $current_path}
  {#if id}
    <slot {id} />
  {:else}
    <slot />
  {/if}
{/if}
