<script>
  import { createEventDispatcher } from 'svelte';
  
  export let services = [];
  const dispatch = createEventDispatcher();

  function handleUpdate(service) {
    dispatch('update', service);  // Emit update event with the service data
  }

  function handleDelete(id) {
    dispatch('delete', id);  // Emit delete event with the service ID
  }
</script>

<h1>Services</h1>

<ul>
  {#each services as service}
    <li>
      <strong>{service.name}</strong>
      <p>{service.description}</p>
      <p>Price: ${service.price}</p>
      <button on:click={() => handleUpdate(service)}>Update</button>  <!-- Update button -->
      <button on:click={() => handleDelete(service.id)}>Delete</button>  <!-- Delete button -->
    </li>
  {/each}
</ul>


<style>
  h1{
    margin-left: 60px;
    font-weight: bold;
  }

  ul{
    margin-left: 40px;
  }
  li{
    border: 0.5px black solid;
    border-radius: 12px;
  }
</style>