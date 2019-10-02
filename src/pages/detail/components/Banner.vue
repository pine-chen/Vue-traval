<template>
	<div>
		<div class="banner" @click="handleBannerClick">
			<img class="banner-img" :src="bannerImg" alt="">
			<div class="banner-info">
				<div class="banner-title">{{this.signtName}}</div>
				<div class="banner-number">
					<span class="iconfont banner-icon">&#xe632;</span>
					{{this.gallaryImgs.length}}
				</div>
			</div>
		</div>
		<fade-animation>
			<common-gallery :imgs="gallaryImgs" v-show="showGallery" @close="handleGalleryClick"></common-gallery>
		</fade-animation>
	</div>
	
</template>

<script>
import CommonGallery from '../../../common/gallery/Gallery'
import FadeAnimation from '../../../common/fade/FadeAnimation'
export default {
	name: 'DetailBanner',
	props: {
		signtName: String,
		bannerImg: String,
		gallaryImgs: Array
	},
	components: {
		CommonGallery,
		FadeAnimation
	},
	data() {
		return {
			showGallery: false
		}
	},
	methods: {
		handleBannerClick() {
			this.showGallery = true
		},
		handleGalleryClick() {
			this.showGallery = false
		}
	}
}
</script>

<style lang="stylus" scoped>
	.banner
		position relative
		overflow: hidden
		height 0
		padding-bottom 55%
		.banner-img
			width 100%
		.banner-info
			display flex
			position absolute
			left 0
			right 0
			bottom 0
			line-height 2.4rem
			color: #fff
			background linear-gradient(top, rgba(0, 0, 0, 0), rgba(0, 0, 0, .8))
			.banner-title
				flex: 1
				font-size .8rem
				padding 0 1rem
			.banner-number
				line-height 1.6rem
				height 1.6rem
				margin-top .5rem
				padding 0 1.8rem
				border-radius .8rem
				background rgba(0, 0, 0, .2)
				font-size .8rem
				.banner-icon
					font-size .8rem
</style>