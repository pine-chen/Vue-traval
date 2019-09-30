<template>
	<div class="header">
		<div class="header-left">
			<div class="iconfont back-icon">&#xe646;</div>
		</div>
		<div class="header-input">
			<span class="iconfont">&#xe62b;</span>
			输入城市/景点/游玩主题
		</div>
		<router-link to='/city'>
			<div class="header-right">
				{{this.city}}
				<span class="iconfont arrow-icon">&#xe64a;</span>
			</div>
		</router-link>
		
	</div>
</template>

<script>
import {mapState} from 'vuex'
export default {
	name: 'HomeHeader',
	computed: {
		...mapState(['city'])
	}
}
</script>

<style scoped lang='stylus'>
@import '~@/assets/styles/varibles.stylus'
	.header
		display: flex
		line-height: 2.6rem
		background: $bgColor
		color: #fff
		.header-left
			width: 3rem
			float: left
			.back-icon
				text-align: center
				font-size: 1.2rem
		.header-input
			flex: 1
			height: 2rem
			line-height: 2rem
			margin-top: .3rem
			padding-left: .5rem
			background: #fff
			border-radius: .3rem
			color:#ccc
		.header-right
			min-width: 3.6rem
			padding 0 .3rem
			float: right
			text-align: center
			color: #fff
			.arrow-icon
				margin-left: -.15rem
				font-size: .9rem
</style>
