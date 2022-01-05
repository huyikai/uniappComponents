<template>
	<!-- 没有封装过多其他参数设置，因为样式非常简单，根据需要自行修改即可 -->
	<view class="switch-box" :style="{background:value?backgroundActive:background}" @click="change">
		<view class="point" :style="{ transform: value ? 'translateX(20px)' : 'translateX(0)' }"></view>
	</view>
</template>

<script>
export default {
	name: 'switch',
	props: {
		// switch状态
		value: {
			default: false,
			type: Boolean
		},
		// switch背景色
		background:{
			default:'#969696'
		},
		//switch打开时背景颜色
		backgroundActive:{
			default:"#f86e00"
		}
	},
	data() {
		return {};
	},
	methods: {
		// 返回switch状态
		change() {
			this.$emit('input', !this.value);
		}
	}
};
</script>

<style lang="scss">
// switch背景
.switch-box {
	background: #969696;
	width: 46px;
	height: 26px;
	border-radius: 26rpx;
	position: relative;

	// 开关圆点
	.point {
		background: #fff;
		width: 18px;
		height: 18px;
		border-radius: 50%;
		position: absolute;
		left: 4px;
		top: 4px;
		transition: transform 0.15s ease;
	}
}
</style>
