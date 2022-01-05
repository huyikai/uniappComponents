<template>
	<view>
		<waterfall v-model="listData" :padding="30">
			<template v-slot:left="{ leftList }">
				<!-- 左侧内容 -->
				<template v-for="(item, index) in leftList">
					<!-- 瀑布流的子内容，可以根据需求自定义修改 -->
					<view class="waterfall-item" :key="index">
						<image class="image" :src="item.image" mode="widthFix"></image>
						<view class="title">{{ item.title }}</view>
					</view>
					<!-- 瀑布流的子内容，可以根据需求自定义修改 End -->
				</template>
			</template>
			<template v-slot:right="{ rightList }">
				<!-- 右侧内容 -->
				<template v-for="(item, index) in rightList">
					<!-- 瀑布流的子内容，可以根据需求自定义修改 -->
					<view class="waterfall-item" :key="index">
						<image class="image" :src="item.image" mode="widthFix"></image>
						<view class="title">{{ item.title }}</view>
					</view>
					<!-- 瀑布流的子内容，可以根据需求自定义修改 End -->
				</template>
			</template>
		</waterfall>
	</view>
</template>

<script>
// 引入组件
import waterfall from '@/components/waterfall.vue';
export default {
	components: {
		waterfall //注册组件
	},
	data() {
		return {
			listData: [] //列表数据
		};
	},
	onLoad() {
		// 初始加载
		this.loadData();
	},
	// 上拉加载
	onReachBottom() {
		this.loadData();
	},
	methods: {
		// 加载数据
		loadData() {
			// 模拟加载数据
			setTimeout(() => {
				for (let i = 0; i < 10; i++) {
					this.listData.push({
						title: `模板数据${i}`,
						image: `/static/template${i + 1}.jpg`
					});
				}
			}, 300);
		}
	}
};
</script>

<style lang="scss">
.waterfall-item {
	width: calc((100vw - 30rpx * 2 - 30rpx) / 2);//计算：(视口宽度 - 左右padding - 中间间隔) / 2
	margin-bottom: 20rpx;
	.image {
		display: block;
		width: 100%;
		border-radius: 12rpx;
		overflow: hidden;
		background: #f5f5f5;
	}
	.title {
		line-height: 64rpx;
		font-size: 32rpx;
		font-weight: bold;
		color: #333;
		padding: 0 10rpx;
		box-sizing: border-box;
	}
}
</style>
