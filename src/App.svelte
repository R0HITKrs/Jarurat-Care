<script>
	import AddServiceForm from './components/AddServiceForm.svelte';
	import ServiceList from './components/ServiceList.svelte';
  
	let services = [
	  { id: 1, name: "General Consultation", description: "Basic health check-up", price: 50 },
	  { id: 2, name: "Blood Test", description: "Complete blood count test", price: 30 },
	];
  
	let isUpdating = false;
	let serviceToUpdate = null;
  
	function addService(event) {
	  services = [...services, event.detail];  // Add new service
	}
  
	function updateService(service) {
	  // Trigger update mode and pre-fill the form with the selected service
	  serviceToUpdate = service;
	  isUpdating = true;
	}
  
	function applyUpdate(updatedService) {
	  services = services.map(s => s.id === updatedService.id ? updatedService : s);  // Apply update
	  serviceToUpdate = null;
	  isUpdating = false;
	}
  
	function deleteService(event) {
	  const id = event.detail;
	  services = services.filter(service => service.id !== id);  // Delete service
	}
  </script>
  
  <!-- Conditionally render add/update form -->
  {#if isUpdating}
	<AddServiceForm service={serviceToUpdate} on:add={applyUpdate} />
  {:else}
	<AddServiceForm on:add={addService} />
  {/if}
  
  <!-- Service list with update and delete functionality -->
  <ServiceList {services} on:update={updateService} on:delete={deleteService} />
  