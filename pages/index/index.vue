<template>
	<view class="content">
		<t-nav-bar fixed disableAutoBack leftText="返回" title="自定义导航栏自定义导航栏自定义导航栏自定义导航栏自定义导航栏自定义导航栏" rightText="分享"
			@clickLeft="onClickLeft" @clickTitle="onClickTitle" @clickRight="onClickRight" />
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
			onClickLeft() {
				console.log('onClickLeft');
				uni.showToast({
					title: 'onClickLeft'
				})
			},
			onClickTitle() {
				console.log('onClickTitle');
				uni.showToast({
					title: 'onClickTitle'
				})
			},
			onClickRight() {
				console.log('onClickRight');
				uni.showToast({
					title: 'onClickRight'
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
	.content {
		height: 2000px;
	}
</style>