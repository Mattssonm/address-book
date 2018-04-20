<template>
	<div>
		<input v-model="newAddress.name" type="text" placeholder="name"/>
    <input v-model="newAddress.address.street" type="text" placeholder="street"/>
    <input v-model="newAddress.address.zip" type="text" placeholder="zip"/>
    <input v-model="newAddress.address.city" type="text" placeholder="city"/>
    <input v-model="newAddress.phone" type="text" placeholder="phone"/>
    <input v-model="newAddress.email" type="text" placeholder="email"/>
    <br>
    <button @click="addAddress" class="button leftButton">Add</button>
    <button @click="closeAddAddress" class="button rightButton">Close</button>
	</div>
</template>

<script>
export default {
	data: function() {
		return {
			newAddress: {
          name: "",
          address: {
            street: "",
            zip: "",
            city: ""
          },
          phone: "",
          email: ""
        },
		};
	},  // data
  methods: {
    addAddress: function() {
      let obj = {
        name: this.newAddress.name,
          address: {
            street: this.newAddress.address.street,
            zip: this.newAddress.address.zip,
            city: this.newAddress.address.city
          },
          phone: this.newAddress.phone,
          email: this.newAddress.email
      };
      this.$emit("send-address", obj);
    },
    closeAddAddress: function() {
      this.$emit("close-add-address")
    }
  }
}
</script>

<style scoped>
  div {
    margin-bottom: 30px;
  }
  input {
    border-radius: 4px;
    font-family: Gandhi;
    border-right: solid 1px gray;
    
  }
</style>