<template>
	<view class="background-editor">
		<view class="editor-title">
			背景
		</view>
		<view class="background-type-list">
			<div v-for="(item) in typeList" :key="item" class="background-type-item"
				:class="{'type-item__selected':selectedType===item}" @click="handleTypeClick(item)">
				{{item}}
			</div>
		</view>
		<view class="background-content">

			<color-selector v-if="selectedType==='纯色'"></color-selector>
			<view class="color-selector" v-else-if="selectedType==='渐变'">
				渐变
			</view>

			<view class="color-selector" v-else-if="selectedType==='网格'">
				网格
			</view>
			<view class="color-selector" v-else-if="selectedType==='点纹'">
				点纹
			</view>
			<view class="color-selector" v-else-if="selectedType==='印花'">
				印花
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name: "background-editor",
		data() {
			return {
				selectedType: "纯色",
				typeList: ["纯色", "图片", "渐变", "网格", "点纹", "印花", ]
			};
		},
		methods: {
			handleTypeClick(item) {
				this.selectedType = item
			},
			handlePureColorSelect(color) {
				console.log(color);
			}
		}
	}
</script>

<style lang="scss">
	.background-editor {
		width: 100%;
		background-color: #fff;
		overflow: hidden;
		box-shadow: 0px -10px 10px -10px rgba(0, 0, 0, 0.1);
		display: flex;
		flex-direction: column;
	}

	.editor-title {
		height: 80rpx;
		line-height: 80rpx;
		font-size: 40rpx;
		text-align: center;
		box-shadow: 0px 3rpx 5rpx rgba(0, 0, 0, 0.1);
	}

	.background-type-list {
		height: 60rpx;
		line-height: 60rpx;
		overflow-x: auto;
		display: flex;

		.background-type-item {
			width: 125rpx;
			font-size: 30rpx;
			text-align: center;

			&.type-item__selected {
				color: $uni-primary;
			}
		}
	}

	.background-content {
		flex: 1;
		background-color: #F8F8F8;
		min-height: 150rpx;
	}
</style>
