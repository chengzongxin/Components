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
		/* 
		空页面类型：
			1. 支持使用组件自带样式
			2. 支持自定义图标，文字样式
			3. 支持插槽，直接添加所需元素
			
		Usage：使用组件内指定类型
			方法一：
			使用 type 指定无页面类型，后续在./props扩展
			nodata：无数据
			nonet：无网络
		
			方法二：
			自定义icon，text，desc
			传入自定义数据即可。例如：
			<t-empty type='nodata' icon="xxx" text="xxx" desc="xxx">
			</t-empty>
		 */
		@Prop({ default: 'nodata' }) readonly type! : string
		@Prop({ default: null }) readonly icon ?: string
		@Prop({ default: null }) readonly text ?: string
		@Prop({ default: null }) readonly desc ?: string

		typeData : object = typeData

		show : boolean = true

		getIcon() {
			return this.icon ? this.icon : this.getValueInTypeData('icon')
		}
		getText() {
			return this.text ? this.text : this.getValueInTypeData('text')
		}
		getDesc() {
			return this.desc ? this.desc : this.getValueInTypeData('desc')
		}
		getValueInTypeData(key : string) {
			let dict = this.typeData[this.type as keyof typeof this.typeData]
			return dict[key as keyof typeof dict]
		}
	}
</script>

<style lang="scss" scoped>
	$t-empty-text-margin-top: 48rpx !default;
	$t-empty-slot-margin-top: 48rpx !default;

	.t-empty {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		min-height: 100vh;

		&__image {
			margin-top: -300rpx;
			width: 200rpx;
			height: 200rpx;
		}

		&__text,
		&__desc {
			display: flex;
			justify-content: center;
			align-items: center;
			margin-top: $t-empty-text-margin-top;
			font-family: PingFangSC-Regular;
		}

		&__text {
			font-size: 28rpx;
			color: #1a1a1a;
		}

		&__desc {
			margin-top: 16rpx;
			font-size: 28rpx;
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