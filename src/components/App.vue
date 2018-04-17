<template>
  <div id="app">
    <list-of-addresses v-bind:addressList="addressList"/>
    <detailed-info/>
    <add-address/>
  </div>
</template>

<script>
import ListOfAddresses from './ListOfAddresses.vue';
import DetailedInfo from './DetailedInfo.vue';
import AddAddress from './AddAddress.vue';
export default {
	name: 'app',
	components: {
		'list-of-addresses': ListOfAddresses,
		'detailed-info': DetailedInfo,
    'add-address': AddAddress
	},
	data: function() {
		return {
      addressList: [
        {
          name: "Bengt Persson",
          address: {
            street: "Götaängsvägen 32",
            zip: "30253",
            city: "Göteborg"
          },
          phone: "0731234567",
          email: "Begnt.Persson@gmail.com"
        },
        {
          name: "Olof Nilsson",
          address: {
            street: "Valandsgatan 23",
            zip: "41123",
            city: "Göteborg"
          },
          phone: "0731223512",
          email: "Olof.Nilsson@gmail.com"
        }
      ]
		};
	},  // data
	methods: {

  } //methods
} //export

</script>

<!-- CSS libraries -->
<style src="normalize.css/normalize.css"></style>

<!-- Global CSS -->
<style>
  #app  {
    text-align: center;
  }

</style>

<!-- Scoped component css -->
<!-- It only affect current component -->
<style scoped>
  #app {
    width: 90%;
    margin: auto;
  }
</style>