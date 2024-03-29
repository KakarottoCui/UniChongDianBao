<template>
	<view class="login">
		<u-navbar :is-fixed="false" :background="{backgroundColor: 'transparent',}" :border-bottom="false"></u-navbar>
		<view class="login-logo">
			<image src="../../static/images/login-logo.png" mode=""></image>
			<view class="title">快速接入充电宝设备</view>
		</view>
		<image class="login-bg" src="https://cqrs.itux.cn/assets/addons/gaga/img/app/18.png" mode=""></image>
		<view class="wx-login" @click="toLogin()" v-if="!isWXlogin">
			授权登录
		</view>
		<view class="wx-login wx-cancle" @click="doBack" v-if="!isWXlogin">
			取消
		</view>

		<view class="footer">
			<u-checkbox-group>
				<u-checkbox v-model="checked" shape="circle" active-color="#6DDE82">
				</u-checkbox>
			</u-checkbox-group>
			<text class="private"> 同意 <text class="color">《嘎嘎快充》</text>、<text
					class="color">《隐私政策》</text>并授权嘎嘎快充获得手机号等信息注册嘎嘎快充账号</text>
		</view>



	</view>
</template>

<script>

	import siteInfo from '@/siteinfo.js'
	export default {
		data() {
			return {
				siteInfo,
				checked: true,
				isLoginPopupVisible: false,
				avatar: '',
				cache_key: '',
				isWXlogin: false,
				userInfo: {},
				token: '',
				isPhoneBox: false,
				back: 0,
				nickName: "",
				avatarUrl: '',
				code: 0
			}
		},
		onLoad(options) {
			this.back = options.back || 0
		},
		computed: {

		},
		onReady() {},
		methods: {
			doBack() {

				uni.navigateBack(-1)
			},
			toLogin() {
				uni.setStorageSync('token', "1321684843")
				uni.redirectTo({
					url: '/pages/app/index'
				})
			},
		}
	}
</script>
<style>
	page {
		position: relative;
		width: 100%;
		height: 100%;
		background-color: #ECF4FD;
	}

	.modal-btns {
		line-height: 88rpx;
		font-size: 26rpx;
		text-align: center;
		width: 200rpx;
	}

	button::after {
		border: none;

	}

	button {
		background-color: #FFFFFF;
	}
</style>
<style lang="scss" scoped>
	.login {
		position: relative;
		width: 100%;
		height: 100%;
		overflow: hidden;

		.login-logo {
			margin-top: 150rpx;
			text-align: center;
			font-size: 40rpx;
			font-family: CTZhongYuanSJ;
			font-weight: 400;
			color: #6DDE82;

			image {
				margin-bottom: 56rpx;
				width: 120rpx;
				height: 90rpx;
			}
		}

		.login-bg {
			margin-top: 56rpx;
			width: 100%;
			height: 360rpx;
		}

		.wx-login {

			margin: 0 auto;
			width: 603rpx;
			height: 80rpx;
			background: #6DDE82;
			text-align: center;
			line-height: 80rpx;
			font-size: 32rpx;
			font-family: PingFang SC;
			font-weight: 500;
			color: #FFFFFF;
			border-radius: 88rpx;
		}

		.wx-cancle {
			margin-top: 40rpx;
			background: #EDEDED;
			color: #BBBBBB;
		}

		.footer {
			display: flex;
			position: absolute;
			left: 60rpx;
			bottom: 100rpx;
			width: 100%;

			.private {
				width: 80%;
				position: absolute;
				left: 50rpx;
				top: -5rpx;
				font-size: 24rpx;
				font-family: PingFang SC;
				font-weight: 400;
				color: #5F646A;
				line-height: 40rpx;
			}

			.color {
				color: #20398A;
			}
		}
	}
</style>
