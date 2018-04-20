<template>
	<div>
    <ul>
      <li @click="selectedInfo(item.name)" v-for="item in address">{{item.name}}</li>
    </ul>
	</div>
</template>

<script>
export default {
  props: ['address'],
	data: function() {
		return {

		};
	},  // data
  methods: {
    selectedInfo: function(name) {
      this.$emit("send-select", {
        name: name
      });
    },
  }
}
</script>

<style scoped>
  ul {
    list-style: none;
    margin-left: 0;
    padding-left: 0;
  }
  
  li {
    font-size: 1.1em;
    margin-bottom: 5px;
  }
</style>