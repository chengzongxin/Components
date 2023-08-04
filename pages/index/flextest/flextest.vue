<template>
	<view class="wrapper">
		<view class="left">1</view>
		<view class="title">2</view>
		<view class="right">3</view>
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

		}
	}
</script>

<style lang="scss" scoped>
	.content {
		height: 2000px;
	}

	.wrapper {
		display: flex;
		text-align: center;

		.left {
			width: 120rpx;
			background-color: aqua;
		}

		.right {
			width: 120rpx;
			background-color: orange;
		}

		.title {
			flex: 1;
			background-color: bisque;
		}
	}
</style>