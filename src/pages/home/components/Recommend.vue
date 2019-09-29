<template>
	<div>
		<div class="recommend-title">热销推荐</div>
		<ul>
			<li class="item border-bottom" v-for="item of list" :key="item.id">
				<div class="item-img-wrapper">
					<img class="item-img" :src="item.imgUrl" alt="">
				</div>
				<div class="item-info">
					<p class="item-title">{{item.title}}</p>
					<p class="item-desc">{{item.desc}}</p>
					<button class="item-button">查看详情</button>
				</div>
			</li>
		</ul>
	</div>
</template>

<script>
	export default {
		name: 'Recommend',
		props: {
			list: Array
		}
	}
</script>

<style lang="stylus" scoped>
@import '~@/assets/styles/mixins.stylus'
	.recommend-title
		margin-top: .4rem
		line-height: 2.5rem
		background: #cccccc4f
		text-indent: 1rem
	.item
		overflow: hidden
		display: flex
		height: 6rem
		.item-img
			width: 5.4rem
			height: 5.4rem
			padding: .3rem
			border-radius: .6rem
		.item-info
			flex: 1
			padding: .3rem
			min-width: 0
			.item-title
				line-height: 1.6rem
				font-size: 1rem
				ellipsis()
			.item-desc
				line-height: 1.1rem
				color: #ccc
				ellipsis()
			.item-button
				line-height: 1.1rem
				margin-top: 1rem
				background: #ff9300
				padding: 0 .3rem
				border: none
				outline: none
				border-radius: .2rem
				color: #fff
</style>