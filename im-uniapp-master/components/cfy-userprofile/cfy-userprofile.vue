<template>
	<view class="card-control" :style="{width: screenWidth+'px'}">
		<view class="card-bg  bg-gradual-green text-white">
			<view class="card-content">
				<view class="padding text-xxl text-cut">
					<view>您好</view>
					<text>{{userInfo.nickName}}</text>
				</view>
				<view class="padding ">
					<view>当前身份</view>
					<text class="text-cut">
						{{level[getValidData]['text']}}
						<!-- {{user.isvalid==true?'认证用户':'访客'}} -->
					</text>
				</view>
				<view>

				</view>
			</view>
			<view class="card-function flex justify-around">
				<block v-if="getValidData==2">
					<view v-for="(item,index) in data3" class="item">
						<text :class="'cuIcon-'+item.icon"></text>
						{{item.text}}
					</view>
				</block>
				<block v-else>

					<view @click="toValid(level[getValidData]['path'])" class="item flex justify-center">
						<text class="cuIcon-profile margin-right-xs"></text>
						{{level[getValidData]['validtext']}}
					</view>
				</block>

				<!-- <uni-grid :show-border="false"  :options="data3" type="oblong" /> -->
			</view>

		</view>
	</view>
</template>

<script>
	import {
		mapState,
		mapGetters
	} from 'vuex'

	export default {
		name:'cfyUserprofile',
		computed: {
			...mapState(['userInfo']),
			...mapGetters(['getValidData']),
			data3: function() {
				console.log('validType', this.userInfo, this.validType)
				var userAuthData = { school: String, sex: String }
				if (this.isValid) {
					userAuthData['sex'] = this.userInfo.gender == 1 ? '男' : '女'
					userAuthData['school'] = this.userInfo.userAuthData['school']['result'][1]
				}

				return [{
					icon: 'friendfill',
					text: '学校：' + userAuthData['school']
				}, {
					icon: 'peoplefill',
					text: '性别：' + userAuthData['sex']
				}]
			},
		},
		props: {
			user: {
				type: Object,
				default: {
					nickname: '未认证用户',
					isvalid: false
				}
			},
		},
		data() {
			// '访客','微信认证','学生认证'
			return {
				level: [{ text: '访客', validtext: '点我登录', 'path': '../login/login' },
					{ text: '微信登录', validtext: '学生认证', 'path': '../reg/reg' },
					{ text: '学生', validtext: '学生认证', 'path': '../reg/reg' },
				],
				screenWidth: this.screenWidth,
				screenHeight: this.screenHeight,
				StatusBar: this.StatusBar,
				CustomBar: this.CustomBar,
			}
		},
		mounted() {
			console.log('mouted')
			var that = this
			// setTimeout(function() {
			// 	that.$forceUpdate()
			// }, 2000);
		},
		updated() {
			var that = this

			console.log('updated')
		},
		methods: {
			toValid(path) {
				console.log('tovalid', )

				uni.navigateTo({
					url: path + '?regtype=reg&url=/pages/home/school'
				})
			}
		},
	}
</script>

<style>
	.card-function {

		padding: 30upx 30upx 0 30upx;
	}

	.card-function .item {}

	.card-content {
		justify-content: space-between;
		display: flex;
		border-bottom: 1px solid #dbdbdb;
		border-top: 0px;
		border-left: 0px;
		border-right: 0px;
	}

	.card-title {
		font-size: 70upx;
		margin-top: 20upx;
		margin-left: 20upx;
	}

	.card-control {
		padding: 20upx;
	}

	.card-id {
		padding: 10upx;
	}

	.card-bg {

		padding: 10upx;
		border-radius: 20upx 20upx;
		min-height: 300upx;
		background-color: #ffffff;
	}
</style>
