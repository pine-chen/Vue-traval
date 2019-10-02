<template>
	<div>
		<div class="item" v-for="(item, index) of categoryList" :key="index">
			<div class="item-title border-bottom">
				<span class="item-title-icon"></span>
				{{item.title}}
			</div>
			<div v-if="item.children" class="item-children">
				<detail-list :categoryList="item.children"></detail-list>
			</div>
		</div>
	</div>
</template>

<script>
export default {
	name: 'DetailList',
	props: {
		categoryList: Array
	}
}
</script>

<style lang="stylus" scoped>
.item-title
	line-height 2.4rem
	font-size 1rem
	padding 0 1rem
	.item-title-icon
		position relative
		left -.1rem
		top .8rem
		display inline-block
		width 2rem
		height 2rem
		background: url(http://s.qunarzz.com/piao/image/touch/sight/detail.png) 0 0 no-repeat
		margin-right: .4rem
		background-size: 2rem 16rem
.item-children
	padding 0 1rem
</style>