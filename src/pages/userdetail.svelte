<script>
  import list from '../store/store';
  export let id;
  let show = false;
  if ($list.length > 0) show = true;
  console.log(id, $list.length);

  function getAddress(address) {
    const { street, suite, city } = address;
    return `${street} - ${suite} - ${city}`;
  }
</script>

{#if show}
  {#each $list as user}
    {#if user.id == id}
      <table>
        <tr>
          <td>ID: </td>
          <td>{user.id}</td>
        </tr>
        <tr>
          <td>Name: </td>
          <td>{user.name}</td>
        </tr>
        <tr>
          <td>Username: </td>
          <td>{user.username}</td>
        </tr>
        <tr>
          <td>Email: </td>
          <td>{user.email}</td>
        </tr>
        <tr>
          <td>Address: </td>
          <td>{getAddress(user.address)}</td>
        </tr>
      </table>
    {/if}
  {/each}
{:else}
  <h1 class="msg">Chưa có dữ liệu</h1>
{/if}
<a href="/users" class="back">Back</a>

<style>
  table,
  th,
  td {
    border: 1px solid black;
    border-collapse: collapse;
  }
  table {
    width: 50%;
  }
  td {
    padding: 5px 0;
    text-align: center;
  }
  .msg {
    line-height: 20px;
    color: #7e7d7da8;
  }
  .back {
    margin-top: 30px;
    padding: 8px 16px;
    border-radius: 5px;
    display: inline-block;
    color: #fff;
    background-color: #5792ff;
  }
  .back:hover {
    box-shadow: rgba(0, 0, 0, 0.12) 0px 1px 3px, rgba(0, 0, 0, 0.24) 0px 1px 2px;
  }
  @media only screen and (min-width: 576px) and (max-width: 980px) {
    table {
      width: 70%;
    }
  }
  @media only screen and (max-width: 575px) {
    table {
      width: 100%;
    }
  }
</style>
