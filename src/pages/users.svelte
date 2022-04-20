<script>
  import { onMount } from 'svelte';
  import list from '../store/store';
  let listUsers = [];
  onMount(() => {
    listUsers = JSON.parse(localStorage.getItem('list')) || [];
    let timeid;
    if (!listUsers || listUsers.length === 0) {
      let url = 'https://jsonplaceholder.typicode.com/users';
      fetch(url)
        .then((response) => response.json())
        .then((json) => {
          localStorage.setItem('list', JSON.stringify(json));
          console.log(json);
          list.update((sate) => [...sate, ...json]);
          timeid = setTimeout(() => {
            listUsers = json;
          }, 0);
        })
        .catch((err) => {
          listUsers = [];
        });
    }

    return () => clearTimeout(timeid);
  });
</script>

<h1>Users</h1>
{#each listUsers as user}
  <div>
    <span>{user.name}</span>
    <a href="/users/{user.id}">Chi tiết</a>
  </div>
{:else}
  <h1>Loading ...</h1>
{/each}

<style>
  div {
    padding: 10px 0;
    display: flex;
    max-width: 300px;
    justify-content: space-between;
  }
</style>
