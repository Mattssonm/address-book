<template>
	<div>
    <button @click="aFunction">ClickMe</button>
	</div>
</template>

<script>
export default {
  props: ["addressList"],
  props: ["name"],
	data: function() {
		return {
      
		};
	},  // data
  methods: {
    aFunction: function () {
      console.log(this.addressList);
    }
  }
}
</script>

<style scoped>

</style>