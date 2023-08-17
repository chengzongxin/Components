<template>
	<view>
		<t-empty type='nodata' v-show="show">
			<button type="primary" @tap="show = false">点击重试</button>
		</t-empty>
		<t-empty type='nonet' v-show="show">
		</t-empty>
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

</style>