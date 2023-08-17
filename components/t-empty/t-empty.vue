<template>
	<view class="t-empty" v-if="show">
		<image class="t-empty__image" :src="getIcon()" mode="widthFix"></image>
		<text class="t-empty__text"> {{ getText() }}</text>
		<text class="t-empty__desc"> {{ getDesc() }}</text>
		<view class="t-empty__wrap" v-if="$slots.default">
			<slot />
		</view>
	</view>
</template>

<script lang="ts">
	import {
		Component,
		Vue,
		Prop
	} from 'vue-property-decorator'
	import { typeData } from './props'
	@Component({})
	export default class TEmpty extends Vue {

		@Prop({ default: 'nodata' }) readonly type! : string

		typeData : object = typeData

		show : boolean = true

		getIcon() {
			return this.getValueInTypeData('icon')
		}
		getText() {
			return this.getValueInTypeData('text')
		}
		getDesc() {
			return this.getValueInTypeData('desc')
		}
		getValueInTypeData(key : string) {
			let dict = this.typeData[this.type as keyof typeof this.typeData]
			return dict[key as keyof typeof dict]
		}

		// 文本样式
		textStyle() {
			const style = {
				color: '#00ff00'
			}
			console.log("style", style)
			return "{ color: '#00ff00', fontSize: '12px' }"
		}
	}
</script>

<style lang="scss" scoped>
	$t-empty-text-margin-top: 24px !default;
	$t-empty-slot-margin-top: 24px !default;

	.t-empty {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		min-height: 100vh;

		&__image {
			width: 100px;
			height: 100px;
		}

		&__text,
		&__desc {
			display: flex;
			justify-content: center;
			align-items: center;
			margin-top: $t-empty-text-margin-top;
		}

		&__text {
			font-size: 14px;
			color: #1a1a1a;
		}

		&__desc {
			margin-top: 8px;
			font-size: 14px;
			color: #aaafbe;
		}

		&__wrap {
			display: flex;
			justify-content: center;
			align-items: center;
			margin-top: $t-empty-slot-margin-top;
		}
	}
</style>