<div id="app">
  <h1>Dashboard</h1>    
    <ul>
    <table class="table">
    <th>key</th>
    <th>value</th>
  {#each data as d}
    {#each d as f}
    <tr>
      <td>{f.key}</td>
      <td class:active>{f.value}</td>
    </tr>
    {/each}
  {/each}
  </table>
</ul>
</div>

<script type="text/javascript">
  import { onMount } from "svelte";
  let active = false 
  let data = [];
  // async data fetching function
  onMount(async function(){
    const response = await fetch(`http://0.0.0.0:8080/get-values`, {
    method : "GET",
    mode: 'cors',
    headers: {
    'Access-Control-Allow-Origin':'*'
    }
    });
    const json = await response.json();
    data = Object.values(json);
  })

</script>

<style>
table {
  border-spacing: 0.5rem;
}
td {
  padding: 0.5rem;
}
th:nth-child(1) { background: hsl(150, 50%, 50%); }
th:nth-child(2) { background: hsl(200, 99%, 50%); }
td:nth-child(1) { background: hsl(150, 50%, 50%); }
td:nth-child(2) { background: hsl(200, 99%, 50%); }



</style>