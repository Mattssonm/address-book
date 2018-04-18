<template>
  <div id="app">
    <list-of-addresses v-on:send-select="recieveSelection" v-bind:address="addressList"/>
    <detailed-info v-bind:selected="selectedAddress"/>
    <add-address v-on:send-address="recieveAddress"/>
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
      ],
      selectedAddress: {
          name: "",
          address: {
            street: "",
            zip: "",
            city: ""
          },
          phone: "",
          email: ""
        }
		};
	},  // data
	methods: {
    recieveSelection: function(obj) {
      this.selectedAddress = this.addressList.find(function(element) {
        return element.name == obj.name;
      });
    },
    recieveAddress: function(obj) {
      this.addressList.push(obj);
    }
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