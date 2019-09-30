<template>
	<div class="list" ref="wrapper">
		<div>
			<div class="area">
				<div class="title border-topbottom">当前城市</div>
				<div class="button-list">
					<div class="button-wrapper">
						<div class="button">{{this.currentCity}}</div>
					</div>
				</div>
			</div>
			<div class="area">
				<div class="title border-topbottom">热门城市</div>
				<div class="button-list">
					<div
						class="button-wrapper"
						v-for="item of hotCities"
						:key="item.id"
						@click="handleCityClick(item.name)"
					>
						<div class="button">{{item.name}}</div>
					</div>
				</div>
			</div>
			<div
				class="area"
			 	v-for="(item, key) of cities"
				:key="key"
				:ref="key"
			>
				<div class="title border-topbottom">{{key}}</div>
				<div class="item-list">
					<div
						class="item border-bottom"
						v-for="innerItem of item"
						:key="innerItem.id"
						@click="handleCityClick(innerItem.name)"
						>
						{{innerItem.name}}
					</div>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
	import BScroll from 'better-scroll'
	import { mapState } from 'vuex'
	export default {
		name: 'CityList',
		props: {
			hotCities: Array,
			cities: Object,
			letter: String
		},
		computed: {
			...mapState({
				currentCity: 'city'
			})
		},
		methods: {
			handleCityClick(city) {
				this.$store.dispatch('changeCity', city)
				this.$router.push('/')
			}
		},
		mounted() {
			this.scroll = new BScroll(this.$refs.wrapper)
		},
		watch: {
			letter() {
				if (this.letter) {
					const element = this.$refs[this.letter][0]
					this.scroll.scrollToElement(element)
				}
			}
		}
	}
</script>

<style lang="stylus" scoped>
	@import '~@/assets/styles/varibles.stylus'
	.border-topbottom
		&:before
			border-color: #ccc
		&:after
			border-color: #ccc
	.border-bottom
		&:before
			border-color: #ccc
		&:after
			border-color: #ccc
	.list
		overflow: hidden
		position: absolute
		top: 4.92rem
		left: 0
		right: 0
		bottom: 0
		.title
			line-height: 1.8rem
			background:#eee
			padding-left: .6rem
			color:#666
			font-size: 1rem 
		.button-list
			overflow: hidden
			padding: .2rem 1.8rem .2rem .2rem
			.button-wrapper
				float: left
				width: 33.33%
				.button
					margin: .3rem
					padding: .3rem 0
					text-align: center
					border: .03rem solid #ccc
					border-radius: .2rem
		.item-list
			.item
				line-height: 2rem
				color: #666
				padding-left: .6rem
</style>