<template>
	<view>
		<view class="grid-box">
			<template v-for="(item, index) in listData">
				<view class="item" :key="index" @click="toPage(item.path)">
					<view class="name">{{ item.name }}</view>
				</view>
			</template>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			listData: [
				{
					name: '瀑布流',
					path: '/pages/components/waterfall/waterfall'
				}
			]
		};
	},
	methods: {
		// 跳转页面
		toPage(path) {
			uni.switchTab({
				url: path,
				fail() {
					uni.navigateTo({
						url: path
					});
				}
			});
		}
	}
};
</script>

<style lang="scss">
.grid-box {
	.item {
		width: calc(100vw / 3);
		height: calc(100vw / 3);
		line-height: calc(100vw / 3);
		text-align: center;
		border-right: 1rpx;
		border-bottom: 1rpx;
		border-style: solid;
		border-color: #f5f5f5;
		box-sizing: border-box;
		font-weight: bold;
		color: #333;
		&:nth-child(3n) {
			border-right: none;
		}
	}
}
</style>
