<script>
  export let hashbang = false;

  import page from "page";
  import { setContext, afterUpdate } from "svelte";
  import { writable } from "svelte/store";

  const current_path = writable("/");
  setContext("current_path", current_path);

  let started = false;
  afterUpdate(() => {
    if (!started) {
      started = true;
      page("*", ctx => {
        $current_path = 'error';
        console.log("NOT FOUND!");
      });
      page.start({ hashbang });
    }
  });
</script>

<slot />
