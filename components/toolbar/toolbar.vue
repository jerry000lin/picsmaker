<template>
	<view class="toolbar">
		<view class="tool-item" @click="handleBackgroudClick">
			<view>
				<image class="tool-icon" src="../../static/editor/beijing.png"></image>
			</view>
			背景
		</view>

		<view class="tool-item">
			<view>
				<image class="tool-icon" src="../../static/editor/tubiao.png"></image>
			</view>
			贴纸
		</view>

		<view class="tool-item">
			<view>
				<image class="tool-icon" src="../../static/editor/wenben.png"></image>
			</view>
			文本
		</view>

		<view class="tool-item">
			<view>
				<image class="tool-icon" src="../../static/editor/neibianju.png"></image>
			</view>
			边框
		</view>

		<view class="tool-item">
			<view>
				<image class="tool-icon" src="../../static/editor/wancheng.png"></image>
			</view>
			完成
		</view>

		<uni-popup ref="popup" type="bottom" mask-background-color="rgba(0,0,0,0)">
			<background-editor></background-editor>
		</uni-popup>
	</view>
</template>

<script>
	export default {
		name: "toolbar",
		data() {
			return {}
		},
		methods: {
			handleBackgroudClick() {
				console.log(this.$refs)
				this.$refs.popup.open('bottom')
			}

		}
	}
</script>

<style lang="scss">
	.toolbar {
		width: 100%;
		height: 180rpx;
		box-shadow: 0px -10px 10px -10px rgba(0, 0, 0, 0.1);
		position: fixed;
		bottom: 0;
		display: flex;

		.tool-item {
			width: 150rpx;
			height: 150rpx;
			box-sizing: border-box;
			text-align: center;
			padding-top: 20rpx;
			font-size: 25rpx;

			.tool-icon {
				width: 50rpx;
				height: 50rpx;
			}
		}
	}
</style>
