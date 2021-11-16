<template>
	<p>Reaction Time : {{ score }} ms</p>
	<div v-if="score < 300">
		<p class="success">Your Brain reflex is great</p>
	</div>
	<div v-else-if="score < 400">
		<p class="manage">Your Brain reflex is good</p>
	</div>
	<div v-else>
		<p class="fail">Your Brain reflex is poor,try again</p>
	</div>
</template>


<script>
	export default {
		props: ['score'],
		data(){
			return{
				rank: null,
			}
		},
	}
</script>


<style>
	.success{
		color: green;
		font-weight: bold;
		font-size: 20px;
	}
	.manage{
		color: yellow;
		font-weight: bold;
		font-size: 20px;
	}
	.fail{
		color: red;
		font-weight: bold;
		font-size: 20px;
	}
</style>