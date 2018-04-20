<template>
  <div id="app">
    <div id="leftPage" class="page">
      <list-of-addresses v-on:send-select="recieveSelection" v-bind:address="addressList"/>
      <button @click="toggleAddAddress" class="button">New</button>
    </div>
    <div id="rightPage" class="page">
      <add-address v-if="showAddAddress" v-on:send-address="recieveAddress" v-on:close-add-address="toggleAddAddress"/>
      <detailed-info v-else v-bind:selected="selectedIndex" v-bind:addressList="addressList" v-on:update-address="updateAddress"/>
    </div>
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
        },
        {
          name: "Evert Ragnhildsson",
          address: {
            street: "Kungsgatan 22",
            zip: "41321",
            city: "Malmö"
          },
          phone: "0731222351",
          email: "Evert@gmail.com"
        },
        {
          name: "Kerstin Nilsson",
          address: {
            street: "Valandsgatan 23",
            zip: "41123",
            city: "Göteborg"
          },
          phone: "0731231419",
          email: "Kerstin.Nilsson@gmail.com"
        }
      ],
      selectedIndex: 0,
      showAddAddress: false
		};
	},  // data
	methods: {
    recieveSelection: function(obj) {
      this.selectedIndex = this.addressList.findIndex(function(element) {
        return element.name == obj.name;
      });

    },
    recieveAddress: function(obj) {
      this.addressList.push(obj);
    }, 
    
    updateAddress: function(obj) {
      this.addressList[this.selectedIndex] = obj;
    },
    toggleAddAddress: function(event) {
      if (this.showAddAddress) {
        this.showAddAddress = false
      } else {
        this.showAddAddress = true;
      }
    }
  } //methods
} //export

</script>

<!-- CSS libraries -->
<style src="normalize.css/normalize.css"></style>
<style src="../main.css"></style>
<!-- Global CSS -->
<style>

</style>

<!-- Scoped component css -->
<!-- It only affect current component -->
<style scoped>
</style>