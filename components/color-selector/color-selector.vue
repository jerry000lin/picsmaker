<template>
	<view class="color-selector">
		<scroll-view scroll-x="true" @scroll.stop>
			<view class="color-list">
				<view class="color-circle  color-picker" @click="showColorPicker"></view>
				<view class="color-circle  color-transparent" @click="colorSelect('transparent')"></view>

				<view class="color-circle" v-for="(item,index) in colorList" :style="{backgroundColor:item}"
					@click="colorSelect(item)"></view>
			</view>
		</scroll-view>
	</view>
</template>

<script>
	export default {
		name: "background-editor",
		data() {
			return {
				colorList: ["#000000", "#696969", "#808080", "#A9A9A9", "#C0C0C0", "#D3D3D3", "#DCDCDC", "#F5F5F5",
					"#FFFFFF", "#800000", "#8B0000", "#B22222", "#A52A2A", "#FF0000", "#CD5C5C", "#BC8F8F", "#F08080",
					"#FFFAFA", "#FA8072", "#FFE4E1", "#FF6347", "#E9967A", "#FF4500", "#FF7F50", "#FFA07A", "#A0522D",
					"#FFF5EE", "#8B4513", "#D2691E", "#F4A460", "#FFDAB9", "#CD853F", "#FAF0E6", "#FF8C00", "#FFE4C4",
					"#DEB887", "#D2B48C", "#FAEBD7", "#FFDEAD", "#FFEBCD", "#FFEFD5", "#FFA500", "#FFE4B5", "#F5DEB3",
					"#FDF5E6", "#FFFAF0", "#DAA520", "#FFF8DC", "#FFD700", "#F0E68C", "#EEE8AA", "#FFFACD", "#BDB76B",
					"#808000", "#FFFF00", "#FFFFE0", "#FFFFF0", "#FAFAD2", "#6B8E23", "#556B2F", "#ADFF2F", "#7CFC00",
					"#7FFF00", "#006400", "#008000", "#228B22", "#00FF00", "#32CD32", "#8FBC8F", "#98FB98", "#90EE90",
					"#F0FFF0", "#2E8B57", "#3CB371", "#00FF7F", "#F5FFFA", "#00FA9A", "#7FFFAA", "#40E0D0", "#20B2AA",
					"#48D1CC", "#008080", "#008B8B", "#2F4F4F", "#00CED1", "#00FFFF", "#00FFFF", "#AFEEEE", "#E1FFFF",
					"#F0FFFF", "#5F9EA0", "#B0E0E6", "#ADD8E6", "#00BFFF", "#87CEEB", "#87CEFA", "#4682B4", "#F0F8FF",
					"#1E90FF", "#708090", "#778899", "#B0C4DE", "#6495ED", "#4169E1", "#000080", "#00008B", "#191970",
					"#0000CD", "#0000FF", "#F8F8FF", "#E6E6FA", "#483D8B", "#6A5ACD", "#7B68EE", "#9370DB", "#8A2BE2",
					"#4B0082", "#9932CC", "#9400D3", "#BA55D3", "#800080", "#8B008B", "#FF00FF", "#FF00FF", "#EE82EE",
					"#DDA0DD", "#D8BFD8", "#DA70D6", "#C71585", "#FF1493", "#FF69B4", "#DB7093", "#FFF0F5", "#DC143C",
					"#FFC0CB", "#FFB6C1"
				]
			};
		},
		methods: {
			showColorPicker() {
				uni.$emit("showColorPickerPopup")
			},
			colorSelect(color) {
				uni.$emit("setBackground", {
					type: "pure",
					value: color
				})
			}
		}
	}
</script>

<style lang="scss">
	.color-selector {

		.color-list {
			height: 150rpx;
			display: flex;
			align-items: center;

			.color-circle {
				flex-shrink: 0;
				margin: 0 25rpx;
				height: 100rpx;
				width: 100rpx;
				border-radius: 50%;
				box-shadow: 0 0 10rpx rgba(0, 0, 0, 0.1);
			}

			.color-picker {
				background: conic-gradient(from 90deg, hsl(0, 100%, 50%), hsl(120, 100%, 50%), hsl(240, 100%, 50%), hsl(360, 100%, 50%));
				position: relative;

				&::after {
					content: "";
					display: block;
					width: 50%;
					height: 50%;
					border-radius: 50%;
					background-color: #fff;
					position: relative;
					top: 50%;
					left: 50%;
					transform: translate(-50%, -50%);
				}
			}

			.color-transparent {
				background-image:
					linear-gradient(45deg, rgba(0, 0, 0, 0.4) 25%, transparent 25%, transparent 75%, rgba(0, 0, 0, 0.4) 75%),
					linear-gradient(45deg, rgba(0, 0, 0, 0.4) 25%, transparent 25%, transparent 75%, rgba(0, 0, 0, 0.4) 75%);
				background-size: 10px 10px;
				background-position: 0 0, 5px 5px;
			}

		}
	}
</style>
