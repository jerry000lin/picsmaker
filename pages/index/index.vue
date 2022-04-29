<template>
	<view class="page-index">
		<button class="start-btn" type="default" @click="start">开始制作吧</button>
		<view class="title">
			模板
		</view>
		<view class="model-list">

			<image class="model-list-item" v-for="i in 10" src="../../static/model/model_template.jpg" mode="widthFix">
			</image>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello'
			}
		},
		onLoad() {

		},
		methods: {
			start() {
				uni.navigateTo({
					url: '/pages/editor/editor'
				})
			}
		}
	}
</script>

<style lang="scss">
	.page-index {
		height: 100%;
		box-sizing: border-box;
		padding: 50rpx;

		.start-btn {
			background-color: $uni-color-primary;
			color: #fff;
			border: 0;
			border-radius: 50rpx;
			height: 100rpx;
			line-height: 100rpx;

			&::after {
				border: 0;
			}
		}

		.title {
			height: 80rpx;
			line-height: 80rpx;
		}

		.model-list {
			padding-left: 50rpx;
			padding-right: 50rpx;
		}

		.model-list-item {
			width: 100%;
			box-sizing: border-box;
			box-shadow: 5rpx 5rpx 10rpx rgba(0, 0, 0, 0.1) ;
		}


	}
</style>
