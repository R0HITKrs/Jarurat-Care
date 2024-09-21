<script>
  import { createEventDispatcher } from 'svelte';

  let name = '';
  let description = '';
  let price = '';

  const dispatch = createEventDispatcher();

  function addService() {
    const newService = { id: Date.now(), name, description, price: parseFloat(price) };
    dispatch('add', newService);  // Emit the new service event
  }
</script>

<!-- Form Structure -->
 <div class="heading"><h1>Jarurat Care</h1></div>
 <h4>Add the Services</h4>
<form class="service-form" on:submit|preventDefault={addService}>
  <div class="form-group">
    <label for="name">Service Name</label>
    <input type="text" id="name" bind:value={name} placeholder="Enter service name" required />
  </div>

  <div class="form-group">
    <label for="description">Service Description</label>
    <textarea id="description" bind:value={description} placeholder="Enter description" required></textarea>
  </div>

  <div class="form-group">
    <label for="price">Price</label>
    <input type="number" id="price" bind:value={price} placeholder="Enter price" required />
  </div>

  <button class="submit-btn" type="submit">Add Service</button>
</form>

<!-- CSS Styling -->
<style>

  .heading{
    text-align: center;
    padding: 5px;
    padding-top: 0;
    margin-top: 0;
    font-size: 38px;
  }

  h4{
    text-align: center;
  }

  .service-form {
    background-color: #f9f9f9;
    border: 0.5px black solid;
    padding: 20px;
    border-radius: 8px;
    max-width: 400px;
    margin: 20px auto;
    box-shadow: rgba(0, 0, 0, 0.05) 0px 0px 0px 1px;  
  }

  .form-group {
    margin-bottom: 15px;
  }

  .form-group label {
    display: block;
    font-weight: bold;
    margin-bottom: 5px;
  }

  .form-group input,
  .form-group textarea {
    width: 100%;
    padding: 12px;
    border: 1px solid #ccc;
    border-radius: 5px;
    font-size: 1rem;
    box-sizing: border-box;
    outline: none;

    &::placeholder{
      font-weight: 300;
      font-size: medium;
    }
  }

  .form-group textarea {
    resize: vertical;
  }

  .submit-btn {
    background-color: #007BFF;
    color: white;
    padding: 10px 20px;
    border: none;
    border-radius: 1000px;
    cursor: pointer;
    font-size: 1rem;
    width: 100%;
  }

  .submit-btn:hover {
    background-color: blue;
  }

  .submit-btn:active {
    background-color: #003f88;
  }

  /* Optional: Responsive styling */
  @media (max-width: 600px) {
    .service-form {
      padding: 15px;
    }
  }
</style>
