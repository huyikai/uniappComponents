<template>
	<view class="container">
		<switch1 v-model="switchStatus1" background="#333"></switch1>
		<switch1 v-model="switchStatus2" backgroundActive="red"></switch1>
	</view>
</template>

<script>
// switch名称冲突，此处使用switch1，按需自定义即可
import switch1 from '@/components/switch.vue';
export default {
	components: {
		switch1
	},
	data() {
		return {
			switchStatus1: false,
			switchStatus2: false
		};
	}
};
</script>

<style lang="scss">
.container {
	padding: 30rpx;
	box-sizing: border-box;
}
</style>
