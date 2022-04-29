<template>
	<view class="editor-page">
		<view class="editor-canvas-container">
			<canvas id="myCanvas" canvas-id="myCanvas"></canvas>
			<view class="user-avatar"></view>
		</view>
		<toolbar @background-change="setBackground"></toolbar>
		<uni-popup ref="colorPickerPopup">
			<color-picker></color-picker>
		</uni-popup>
	</view>
</template>

<script>
	let context = null
	export default {
		provide: {
			editor: this
		},
		data() {
			return {
				background: {
					type: "pure",
					value: "#ffffff"
				}
			}
		},
		methods: {
			setBackground: function(background) {
				console.log(background);
				context.beginPath()
				context.rect(0, 0, this.canvasHeight, this.canvasWidth)
				context.setFillStyle(background.value)
				context.fill()
				context.draw()
			},
			showColorPickerPopup() {
				this.$refs.colorPickerPopup.open()
			}
		},
		onReady: function() {
			context = uni.createCanvasContext('myCanvas', this)
			this.canvasWidth = this.canvasHeight = uni.upx2px(750)
			this.setBackground(this.background)

			uni.$on("setBackground", this.setBackground)
			uni.$on("showColorPickerPopup", this.showColorPickerPopup)
		},
		onUnload() {
			uni.$off("setBackground")
		}
	}
</script>

<style lang="scss">
	.editor-page {
		background: linear-gradient(to bottom, #efeff4, white);
		height: 100%;
		position: relative;



		.editor-canvas-container {
			position: relative;
			height: 750rpx;
			width: 750rpx;
			background-image:
				linear-gradient(45deg, rgba(0, 0, 0, 0.4) 25%, transparent 25%, transparent 75%, rgba(0, 0, 0, 0.4) 75%),
				linear-gradient(45deg, rgba(0, 0, 0, 0.4) 25%, transparent 25%, transparent 75%, rgba(0, 0, 0, 0.4) 75%);
			background-size: 10px 10px;
			background-position: 0 0, 5px 5px;

			#myCanvas {
				width: 750rpx;
				height: 750rpx;
			}

			.user-avatar {
				position: absolute;
				width: 133rpx;
				height: 133rpx;
				background-color: #000;
				right: 24rpx;
				bottom: -40rpx;
				border-radius: 13rpx;
			}
		}
	}
</style>
