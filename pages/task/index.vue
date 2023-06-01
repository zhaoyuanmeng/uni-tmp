<template>
	<view class="content">
		<!-- <div class="title">
			<img src="../../static/lb.png">
			<p>司机在执行运输任务时，需要手动点击“打卡”进行位置提示</p>
		</div> -->
		<div class="card">
			<div class="card_content">
				<u-swiper :list="list1" height="180"></u-swiper>
			</div>
		</div>
		<div class="tabs">
			<u-sticky bgColor="#fff" @fixed="handleFiexed">
				<div class="tabs_header">
					<div class="tabs_header_items" v-for="item in tabs" @click="handelActive(item.index)"
						:class="{ active: active == item.index }">
						{{item.name}}
					</div>
				</div>
			</u-sticky>
			<div class="tabs_content">

				<u-transition :show="active == 1" mode="slide-left">
					<view class="transition">
						<div class="tab1_content">
							<div class="search">
								<input type="text" placeholder="待签单">
							</div>
							<div class="dan_card">
							</div>
							<div class="dan_card">
							</div>
							<div class="dan_card">
							</div>
						</div>
					</view>
				</u-transition>
				<u-transition :show="active == 2" mode="slide-left">
					<view class="transition">
						<div class="tab1_content">
							<div class="search">
								<input type="text" placeholder="进行中">
							</div>
							<div class="dan_card">
							</div>
							<div class="dan_card">
							</div>
							<div class="dan_card">
							</div>
						</div>
					</view>
				</u-transition>
				<u-transition :show="active == 3" mode="slide-left">
					<view class="transition">
						<div class="tab1_content">
							<div class="search">
								<input type="text" placeholder="已完成">
							</div>
							<div class="dan_card">
							</div>
							<div class="dan_card">
							</div>
							<div class="dan_card">
							</div>
						</div>
					</view>
				</u-transition>

			</div>
		</div>
		
		<u-tabbar @change="name => value6 = name" :fixed="true" :placeholder="true" :safeAreaInsetBottom="true">
			<u-tabbar-item text="任务管理" icon="home"></u-tabbar-item>
			<u-tabbar-item text="打卡" icon="play-right"></u-tabbar-item>
			<u-tabbar-item text="个人中心" icon="account"></u-tabbar-item>
		</u-tabbar>
	</view>
</template>

<script>
	import {
		getUserInfo,
		userLogin
	} from "@/api/user.js"
	export default {
		data() {
			return {
				list1: [
					'https://cdn.uviewui.com/uview/swiper/swiper1.png',
					'https://cdn.uviewui.com/uview/swiper/swiper2.png',
					'https://cdn.uviewui.com/uview/swiper/swiper3.png',
				],
				title: 'Hello',
				active: 1,
				tabs: [{
						index: 1,
						name: '待签单'
					},
					{
						index: 2,
						name: '进行中'
					},
					{
						index: 3,
						name: '已完成'
					}
				]
			}
		},
		onLoad() {},
		methods: {
			handelActive(idx) {
				this.active = idx
			},
			change(data) {
				this.current = data.index;
			},
			handleFiexed() {
				console.log('aaaaaaaaaaaaa')
			}
		}
	}
</script>

<style lang="scss">
	.content {
		.title {
			display: flex;
			justify-content: center;
			align-items: center;
			gap: 8px;
			background-color: #f4a671;
			img {
				height: 20px;
			}

			p {
				font-size: 12px;
				color: #fff;
			}
		}

		.card {
			padding: 15px;
			background: linear-gradient(180deg, #EF7E33 0%, rgba(243, 148, 80, 0) 100%);

			.card_content {
				height: 180px;
				background: #FFFFFF;
				box-shadow: 0px 3px 10px 1px rgba(0, 0, 0, 0.08);
				border-radius: 10px 10px 10px 10px;
				opacity: 1;
				z-index: 99;
			}
		}

		.tabs {

			&_header {
				display: flex;
				padding: 20px 36px;
				opacity: 1;
				align-items: center;
				justify-content: space-between;
				box-shadow: 0px 3px 10px 1px rgba(0, 0, 0, 0.08);

				&_items {
					font-size: 16px;
					font-weight: 400;
					color: #999999;
					cursor: pointer;
					position: relative;
					transition: all .1s;

					&.active {
						color: #333333;
						font-weight: 500;
						transform: scale(1.05);

						&::before {
							width: 27px;
							content: "";
							display: inline-block;
							height: 4px;
							background: #EE782B;
							border-radius: 3px 3px 3px 3px;
							opacity: 1;
							position: absolute;
							top: 25px;
							left: 10px;
						}
					}

				}
			}

			&_content {
				padding: 10px 15px;

				.tab1_content {

					.search {
						padding: 0 20px;

						input {
							color: #7d8592;
							font-size: 16px;
							border-radius: 18px 18px 18px 18px;
							opacity: 1;
							height: 36px;
							line-height: 36px;
							padding-left: 50px;
							border: 1px solid #DCDCDC;
						}
					}

					.dan_card {
						width: 100%;
						margin-top: 10px;
						height: 205px;
						background: #FFFFFF;
						box-shadow: 0px 2px 10px 1px rgba(0, 0, 0, 0.08);
						border-radius: 13px 13px 13px 13px;
						opacity: 1;
					}
				}
			}

		}
	}
</style>