<template>
	<div class="content">
		<div>登录页面</div>
		<button @click="doLogin">登录</button>
	</div>
</template>

<script>
	import {getUserInfo,userLogin} from "@/api/user.js"
	export default {
		data() {
			return {
				title: 'Hello'
			}
		},
		onLoad() {
		},
		methods: {
		doLogin(){
			console.log('aaaaaaaa')
			uni.navigateTo({
				url: '/pages/test/index'
			});
		}
		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
</style>
