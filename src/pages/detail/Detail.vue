<template>
	<div>
		<detail-banner 
			:signtName="signtName"
			:bannerImg="bannerImg"
			:gallaryImgs="gallaryImgs"
		>	
		</detail-banner>
		<detail-header></detail-header>
		<div class="content">
			<detail-list :categoryList="categoryList"></detail-list>
		</div>
	</div>
</template>

<script>
import axios from 'axios'
import DetailBanner from './components/Banner'
import DetailHeader from './components/Header'
import DetailList from './components/List'
export default {
	name: 'Detail',
	components: {
		DetailBanner,
		DetailHeader,
		DetailList
	},
	data() {
		return{
			signtName: '',
			bannerImg: '',
			gallaryImgs: [],
			categoryList: []
		}
	},
	methods: {
		getDetailInfo() {
			axios.get('/mock/detail.json?id=',{
				params: {
					id: this.$route.params.id
				}
			})
			.then(this.handleGetDataSucc)
		},
		handleGetDataSucc(res) {
			res = res.data
			if (res.ret && res.data) {
				const data = res.data
				this.signtName = data.signtName
				this.bannerImg = data.bannerImg
				this.gallaryImgs = data.gallaryImgs
				this.categoryList = data.categoryList
			}
		}
	},
	mounted() {
		this.getDetailInfo()
	}
}
</script>

<style lang="stylus" scoped>
	.content
		height 100rem
</style>