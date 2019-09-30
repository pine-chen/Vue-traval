<template>
	<div class="header">
		城市选择
		<router-link to='/'>
			<div class="iconfont header-back">&#xe646;</div>
		</router-link>
	</div>
</template>

<script>
	export default {
		name: 'CityHeader'
	}
</script>

<style lang="stylus" scoped>
@import '~@/assets/styles/varibles.stylus'
	.header
		position: relative
		overflow: hidden
		height: 2.5rem
		line-height: 2.5rem
		text-align: center
		color: #fff
		background: $bgColor
		font-size: 1rem
		.header-back
			position: absolute
			top: 0
			left: 0
			width: 3rem
			text-align: center	
			font-size: 1.2rem
			color: #fff
</style>