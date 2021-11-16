<template>
	<div v-if="showBlock" class="block" @click="stopTimer">
		Click here fast
	</div>
</template>


<script>
	export default {
		props: ['delay'],
		data(){
			return{
				showBlock: false,
				timer: null,
				reactionTime: 0,
			}
		},
		mounted(){
			setTimeout(() => {
				this.showBlock = true
				this.startTimer()
			}, this.delay)
			console.log('component mounted')
		},

		methods: {
			startTimer(){
				this.timer = setInterval(() => {
					this.reactionTime += 10
				}, 10)
			},
			stopTimer(){
				clearInterval(this.timer)
				this.$emit('end', this.reactionTime)
			}
		}
	}
</script>


<style>
	.block{
		width: 400px;
		border-radius: 20px;
		color: white;
		text-align: center;
		margin: 25px auto;
		padding: 100px 0;
		background: #0faf87;
	}
</style>