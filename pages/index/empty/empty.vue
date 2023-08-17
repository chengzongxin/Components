<template>
	<view>
		<!-- 		<t-empty type='nodata' v-show="show"
			icon="https://mp-f03fb0ab-2438-4197-be6d-9c6d1101d525.cdn.bspapp.com/images/1691290861616-red-girl.jpg"
			text="123" desc="456">
			<button type="primary" @tap="show = false">点击重试</button>
		</t-empty> -->
		<t-empty type='nonet' v-show="show">
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