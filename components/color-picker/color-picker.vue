<template>
	<view class="color-picker">
		<view class="title">
			颜色
		</view>
	</view>
</template>

<script>
	export default {
		name: "color-picker",
		data() {
			return {
				showColor
			};
		}
	}
</script>

<style lang="scss">
	.color-picker {
		width: 600rpx;
		height: 1000rpx;
		background-color: #282828;
		color: #fff;

		.title {
			font-size: $title-font-size;
			height: 50px;
			line-height: 50px;
			text-align: center;
		}
	}
</style>
