<template>
	<view class="content">

		<t-nav-bar :fixed="true" disableAutoBack leftText="返回" title="自定义导航栏自定义导航栏自定义导航栏自定义导航栏自定义导航栏自定义导航栏"
			rightText="分享" @clickLeft="onClickLeft" @clickTitle="onClickTitle" @clickRight="onClickRight" border
			shadow />

		<view class="content-area">
			<text>暗黑模式</text>
			<t-nav-bar :fixed="false" title="暗黑模式" dark />
		</view>

		<view class="content-area">
			<text>自定义插槽</text>
			<t-nav-bar :fixed="false">
				<template #left>
					<button type="warn">left</button>
				</template>
				<template>
					<button type="default">123456</button>
				</template>
				<template #right>
					<button type="primary">right</button>
				</template>
			</t-nav-bar>
		</view>


		<view class="content-area">
			<text>自定义高度背景</text>
			<t-nav-bar :fixed="false" title="自定义高度背景" rightText="分享" @clickRight="onClickRight" color="blue"
				background-color="orange" height="66px" />
		</view>


	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello',
				red: '#FF0000'
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
			onClickRight(e) {
				console.log('onClickRight', e);
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
		box-sizing: border-box;
		background-color: $uni-bg-color-grey;
	}

	.top {
		// margin-top: 10px;
	}

	.nav {
		// margin-top: 100px;
	}

	.cus-nav-h {
		height: 66px;
		background-color: red;
	}

	.nav-2 {
		margin-top: 20px;
	}

	.content-area {
		padding-top: 60px;
		overflow: hidden;
		display: flex;
		flex-direction: column;
		justify-content: space-around;

		text {
			margin-bottom: 10px;
			font-size: 20px;
		}
	}

	.content-area:nth-child(2) {
		padding-top: 100px;
		overflow: hidden;
	}
</style>