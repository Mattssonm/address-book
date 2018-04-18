<template>
	<div>
    <h3>More info</h3>
    <p>Name: {{selected.name}}</p>
    <p>Address: {{selected.address.street}} {{selected.address.zip}} {{selected.address.city}}</p>
    <p>Phone: {{selected.phone}}</p>
    <p>Email: {{selected.email}}</p>
	</div>
</template>
<script>
export default {
  props: ['selected'],
	data: function() {
		return {
      
		};
	}  // data
}
</script>

<style scoped>
</style>