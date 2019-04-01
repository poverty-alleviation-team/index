<template>
	<div class="index">
		<transition name="fade">
			<div style="height: 100%; width: 50%;background-color: #42B983;position: absolute;left: 0;" v-if="load"></div>
		</transition>
		<transition name="fade3">
			<div v-if="load" style="z-index: 20;">
				<el-progress v-if="jindu!=100" type="circle" :percentage="jindu" color="#8e71c7"></el-progress>
				<el-button v-else type="primary" @click="unload">请开始你的表演</el-button>
			</div>
		</transition>
		<transition name="fade2">
			<div style="height: 100%; width: 50%;background-color: brown;position: absolute;right: 0;" v-if="load"></div>
		</transition>
	</div>
</template>

<script>
	export default {
		data() {
			return {
				load: true,
				jindu: 0,
				inv: null
			}
		},
		created() {
			this.inv = setInterval(() => {
				this.jindu += 10
				if (this.jindu == 100) {
					clearInterval(this.inv);
				}
			}, 200)
		},
		methods: {
			unload(){
				this.load = false
			}
		}
	}
</script>

<style>
	.index {
		display: flex;
		position: relative;
		align-items: center;
		justify-content: center;
	}

	.fade-enter-active,
	.fade-leave-active {
		transition: all .5s;
	}

	.fade-enter,
	.fade-leave-to {
		transform: translateX(-100%);
	}

	.fade2-enter-active,
	.fade2-leave-active {
		transition: all .5s;
	}

	.fade2-enter,
	.fade2-leave-to {
		transform: translateX(100%);
	}

	.fade3-enter-active,
	.fade3-leave-active {
		transition: all .5s;
	}

	.fade3-enter,
	.fade3-leave-to {
		opacity: 0;
	}
</style>
