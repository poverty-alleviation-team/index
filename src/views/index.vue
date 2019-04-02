<template>
	<div class="index">
		<div class="loadDiv" v-if="loadiv">
			<transition name="fade">
				<div style="height: 100%; width: 50%;background-color: #42B983;position: absolute;left: 0;top: 0;" v-if="load"></div>
			</transition>
			<transition name="fade3">
				<div v-if="load" style="z-index: 20;">
					<el-progress v-if="jindu!=100" type="circle" :percentage="jindu" color="#8e71c7"></el-progress>
					<el-button v-else type="primary" @click="unload">请开始你的表演</el-button>
				</div>
			</transition>
			<transition name="fade2">
				<div style="height: 100%; width: 50%;background-color: brown;position: absolute;right: 0;top: 0;" v-if="load"></div>
			</transition>
		</div>

		<div class="content">
			<p v-for="k in 2000" :key='k'>a</p>
		</div>
	</div>
</template>

<script>
	export default {
		watch:{
			load(n){
				if(!n){
					setTimeout(()=>{
						this.loadiv = false;
					},500)
				}
			}
		},
		data() {
			return {
				load: true,
				loadiv:true,
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
			unload() {
				this.load = false
			}
		}
	}
</script>

<style>
	.index {
		position: relative;
	}

	.loadDiv {
		position: absolute;
		width: 100%;
		height: 100%;
		display: flex;
		align-items: center;
		justify-content: center;
		z-index: 2;
	}

	.content {
		margin-left: 15%;
		width: 70%;
		height: 100%;
		overflow-y: auto;
		box-shadow: 0 0 1.875rem 0.625rem aqua;
	}
	
	.content::-webkit-scrollbar{
		width: 0.625rem;
	}
	/*滚动条里面滑块*/
	.content::-webkit-scrollbar-thumb {
        border-radius: 10px;
         -webkit-box-shadow: inset 0 0 5px rgba(0,0,0,0.2);
        background: #409EFF;
    }
	/*滚动条里面轨道*/
	.content::-webkit-scrollbar-track {
        -webkit-box-shadow: inset 0 0 5px rgba(0,0,0,0.2);
        border-radius: 0.3125rem;
        background: #EDEDED;
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
