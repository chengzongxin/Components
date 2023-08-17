<template>
	<view>
		<t-empty type='nonet' v-show="show">
			<!-- 自定义插槽 -->
			<button type="primary" @tap="show = false">点击重试</button>
		</t-empty>
		<view class="content" v-show="!show">
			<text> 现在有内容 </text>
			<text> 现在有内容 </text>
			<text> 现在有内容 </text>
			<text> 现在有内容 </text>
			<text> 现在有内容 </text>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				show: true
			}
		},
		methods: {
			hide() {
				this.show = false
				console.log('click show = ', this.show)
			}
		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		min-height: 100vh;
	}
</style>