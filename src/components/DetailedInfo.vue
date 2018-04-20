<template>
	<div>
    <p>Name: 
      <input v-model="inputAddress.name" v-if="clickedInfo.name" @mouseout="spanSwitch('name')" type="text" /> 
      <span v-else @click="inputSwitch('name')">{{addressList[selected].name}}</span>
    </p>
    <p>Street: 
      <input v-model="inputAddress.address.street" v-if="clickedInfo.street" @mouseout="spanSwitch('street')" type="text" /> 
      <span @click="inputSwitch('street')" v-else>{{addressList[selected].address.street}}</span>
    </p>
    <p>Zip: 
      <input v-model="inputAddress.address.zip" v-if="clickedInfo.zip" @mouseout="spanSwitch('zip')" type="text"/> 
      <span @click="inputSwitch('zip')" v-else>{{addressList[selected].address.zip}}</span>
    </p>
    <p>City: 
      <input v-model="inputAddress.address.city" v-if="clickedInfo.city" @mouseout="spanSwitch('city')" type="text"/> 
      <span @click="inputSwitch('city')" v-else>{{addressList[selected].address.city}}</span>
    </p>
    <p>Phone: 
      <input v-model="inputAddress.phone" v-if="clickedInfo.phone" @mouseout="spanSwitch('phone')" type="text"/> 
      <span @click="inputSwitch('phone')" v-else>{{addressList[selected].phone}}</span>
    </p>
    <p>Email: 
      <input v-model="inputAddress.email" v-if="clickedInfo.email" @mouseout="spanSwitch('email')" type="text"/> 
      <span @click="inputSwitch('email')" v-else>{{addressList[selected].email}}</span>
    </p>
	</div>
</template>
<script>
export default {
  props: ['selected', "addressList"],
	data: function() {
		return {
      clickedInfo: {
        name: false,
        street: false,
        zip: false,
        city: false,
        phone: false,
        email: false
      },
      inputAddress: {
         name: this.addressList[this.selected].name,
          address: {
            street: this.addressList[this.selected].address.street,
            zip: this.addressList[this.selected].address.zip,
            city: this.addressList[this.selected].address.city
          },
          phone: this.addressList[this.selected].phone,
          email: this.addressList[this.selected].email
      }
		};
	},  // data
  methods: {
    inputSwitch: function(info)  {
      this.clickedInfo[info] = true;
      
    }, 
    spanSwitch: function(info) {
      this.clickedInfo[info] = false;
      this.updateAddress();

    }, 
    updateInputValues: function () {
      this.inputAddress = {
        name: this.addressList[this.selected].name,
        address: {
          street: this.addressList[this.selected].address.street,
          zip: this.addressList[this.selected].address.zip,
          city: this.addressList[this.selected].address.city
        },
        phone: this.addressList[this.selected].phone,
        email: this.addressList[this.selected].email
      }
    }, 
    updateAddress: function () {
      this.$emit("update-address", this.inputAddress);
    }
  }, //methods
  watch: { 
    selected: function(newVal, oldVal) {
      console.log('Prop changed: ', newVal, ' | was: ', oldVal)
      this.updateInputValues();
    }
  } 
} //export default
</script>

<style scoped>
</style>