<template>
	<div class="preview">
		<ul>
			<li v-for="gif in gifs">
				<img :src="gif.images.fixed_height.url">

				<button v-on:click="copyUrl(gif.images.fixed_height.url)">Url Copy</button>
			</li>
		</ul>
	</div>
</template>

<script>
	export default {
		props: [ 'gifs' ],
		data() {
			return {
				url: ''
			}
		},
		methods: {
			copyUrl(requesturl) {
				this.url = requesturl;
				alert(this.url)
				console.log(this.url)
			}
		}
	}
</script>

<style>
	li {
		list-style: none;
		float: left;
		margin: 15px;
	}
</style>
