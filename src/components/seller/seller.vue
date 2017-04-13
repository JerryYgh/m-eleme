<template>
	<div class="ratings">
		<div class="top-wrapper white">
			<div class="base">
				<div class="left">
					<h3 class="title">{{ seller.name}}</h3>
					<div class="counts">
						<div class="star-wrapper">
							<star :size="36" :score="seller.score"></star>
						</div>
						<span></span>
						<span>月售{{ seller.sellCount}}单</span>
					</div>
				</div>
				<div class="right">
					
				</div>
			</div>
			<div class="delivery-wrapper">
				<div class="minPrice item border-right">
					<h5>起送价</h5>
					<div class="notice">{{seller.minPrice}}<span>元</span></div>
				</div>
				<div class="deliveryPrice item border-right">
					<h5>商家配送</h5>
					<div class="notice">{{seller.deliveryPrice}}<span>元</span></div>
				</div>
				<div class="deliveryTime item">
					<h5>平均配送时间</h5>
					<div class="notice">{{seller.deliveryTime}}<span>分钟</span></div>
				</div>
			</div>
		</div>
		<div class="avtivities-wrapper white">
			<h3 class="title">公告与活动</h3>
			<p class="bulletin">{{seller.bulletin}}</p>
			<ul v-if="seller.supports" class="supports">
				<li class="support-item border-top-1px" v-for="(item,index) in seller.supports">
					<span class="icon" :class="classMap[seller.supports[index].type]"></span>
					<span class="text">{{seller.supports[index].description}}</span>
				</li>
			</ul>
		</div>
		<div class="pics-wrapper white">
			<h3 class="title">商家实景</h3>
			<div class="content" v-if="seller.pics">
				<ul>
					<li v-for="(item,index) in seller.pics">
						<img :src="item" alt="">
					</li>
				</ul>
			</div>
		</div>
		<div class="infos-wrapper white">
			<h3 class="title">商家信息</h3>
			<div class="infos" v-if="seller.infos">
				<ul>
					<li v-for="(item,index) in seller.infos">{{item}}</li>
				</ul>
			</div>
		</div>
	</div>
</template>

<script type="test/ecmascript-6">
	import star from './../star/star'
	export default{
		name: 'ratings',
		props: {
			seller: {
				type: Object
			}
		},
		data() {
			return {
				classMap: ['decrease', 'discount', 'special', 'invoice', 'guarantee']
			}
		},
		components: {
			star
		}
	};
</script>

<style lang="stylus" rel="stylesheet/stylus">
	@import "../../common/stylus/mixin"
	.ratings
		background: #f3f5f7
		.top-wrapper
			padding: 18px 0
			border-bottom-1px(rgba(7,17,27,0.1))
			.base
				display:flex
				justify-content: space-between
				margin: 0 18px
				padding-bottom: 18px
				border-bottom-1px(rgba(7,17,27,0.1))
				.counts
					margin-top: 8px
					.star-wrapper
						display: inline-block
					span
						font-size: 10px
						color: rgb(77,85,93)
			.delivery-wrapper
				display: flex
				.item
					flex: 1
					margin-top: 18px
					text-align: center
					&.border-right
						border-right: 1px solid rgba(7,17,27,0.1)
					h5
						font-size: 10px
						color: rgb(147,153,159)
					.notice
						margin-top: 5px
						font-size: 24px
						font-weight: 200
						color: rgb(7,17,27)
						span
							font-size: 10px
		.avtivities-wrapper, .pics-wrapper, .infos-wrapper
			margin-top: 16px
			border-top-1px(rgba(7,17,27,0.1))
			border-bottom-1px(rgba(7,17,27,0.1))
		.avtivities-wrapper
			padding: 18px 18px 0;
			.title
				font-size: 14px
				color: rgb(7,17,27)
			.bulletin
				margin: 8px 0 16px
				padding: 0 12px
				line-height: 24px
				font-size: 12px
				font-weight: 200
				text-align: justify
				color: rgb(240,20,20)
			.supports
				li
					border-top-1px(rgba(7,17,27,0.1))
					padding: 16px 12px
					font-size: 12px
					color: rgb(7,17,27)
					.icon
						vertical-align: top
						display: inline-block
						width: 12px
						height: 12px
						margin-right: 4px
						background-size: 12px 12px
						background-repeat: no-repeat
						&.decrease
							bg-image("decrease_4")
						&.discount
							bg-image("discount_4")
						&.guarantee
							bg-image("guarantee_4")
						&.invoice
							bg-image("invoice_4")
						&.special
							bg-image("special_4") 
		.pics-wrapper
			padding: 18px 0 18px 18px;
		.infos-wrapper
			padding: 18px 18px 0 18px;
			.infos
				margin-top: 12px
				li 
					border-top-1px(rgba(7,17,27,0.1))
					line-height: 16px
					padding: 16px 12px
					font-size: 12px
					color: rgb(7,17,27)


</style>
