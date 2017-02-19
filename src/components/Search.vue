<template>
	<div class="search">
		<input type="text" v-model="query" v-on:keypress.enter="handleSearch">
		<button v-on:click="handleSearch">Giphy Search</button>
	</div>
</template>

<script>
	export default {
		data() {
			return {
				query: ''
			}
		},
		methods: {
			handleSearch() {
				this.$emit('SearchRequested' ,this.query);
			}
		}
	}
</script>

<style>
	.search input {
		border-radius: 10px;
		border:2px solid #CCC;
		width: 200px;
		height: 25px;
	}
	.search button {
		border-radius: 10px;
		border:2px solid #BBB;
		height: 30px;
		margin-left: 10px;
	}
</style>