<template>
	<div>
		<router-link tag="div" to="/" class="header-abs" v-show="showAbs">
			<div class="iconfont header-abs-back">&#xe646;</div>
		</router-link>
		<div class="header-fixed" v-show="!showAbs" :style="opacityStyle">
			<router-link to="/">
				<div class="iconfont header-fixed-back">&#xe646;</div>
			</router-link>
			景点详情
		</div>
	</div>
</template>

<script>
export default {
	name: 'DetailHeader',
	data() {
		return {
			showAbs: true,
			opacityStyle: {
				opacity: 0
			}
		}
	},
	methods: {
		handleScroll() {
			const top = document.documentElement.scrollTop
			if (top > 10 ) {
				let opacity = top / 60
				opacity = opacity > 1 ? 1 : opacity
				this.opacityStyle = {
					opacity: opacity
				}
				this.showAbs = false
			}else{
				this.showAbs = true
			}
		}
	},
	activated() {
		window.addEventListener('scroll', this.handleScroll)
	},
	deactivated() {
		window.removeEventListener('scroll', this.handleScroll)
	}
}
</script>

<style lang="stylus" scoped>
@import '~@/assets/styles/varibles.stylus'
	.header-abs
		position absolute
		left .8rem
		top .8rem
		width 1.8rem
		height 1.8rem
		line-height 1.8rem
		border-radius .9rem
		text-align center
		background rgba(0, 0, 0, .8)
		.header-abs-back
			color: #fff
			font-size 1rem
	.header-fixed
		z-index 2
		position: fixed
		top 0
		left 0
		right 0
		height: 2.5rem
		line-height: 2.5rem
		text-align: center
		color: #fff
		background: $bgColor
		font-size: 1rem
		.header-fixed-back
			position: absolute
			top: 0
			left: 0
			width: 3rem
			text-align: center	
			font-size: 1.2rem
			color: #fff
</style>