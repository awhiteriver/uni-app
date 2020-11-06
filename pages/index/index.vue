<template>
	<view class="content">
		<view class="top-bar">
			<view class="top-bar-left">
				<image src="../../static/test/whiteriver.png"></image>
			</view>
			<view class="top-bar-center">
				<image src="" alt="chatapp" class="logo"></image>
			</view>
			<view class="top-bar-right">
				<view class="search"><image src="../../static/icon/search@2x.png"></image></view>
				<view class="add"><image src="../../static/icon/add group@2x.png"></image></view>
			</view>
		</view>
		<view class="main">
			<view class="apply">
				<view class="friend-list">
					<view class="friend-list-left">
						<text class="tip">1</text>
						<image src="../../static/images/index/apply.png"></image>
					</view>
					<view class="friend-list-right">
						<view class="top">
							<view class="name">好友申请</view>
							<view class="time"></view>
						</view>
						<view class="news">
							希望人没事,希望人没事,希望人没事,希望人没事，希望人没事，希望人没事，希望人没事
						</view>
					</view>
				</view>
			</view>
			<view class="friends">
				<view class="friend-list" v-for="(item,index) in friends" :keys="item.id">
					<view class="friend-list-left">
						<text class="tip">{{item.tip}}</text>
						<image :src="item.imgurl"></image>
					</view>
					<view class="friend-list-right">
						<view class="top">
							<view class="name">{{item.name}}</view>
							<view class="time">{{changeTime(item.time)}}</view>
						</view>
						<view class="news">
							{{item.news}}
						</view>
					</view>
				</view>
			</view>
		</view>
		
	</view>
</template>

<script>
	import data from '../../common/js/data.js'
	import myfunction from '../../common/js/myfunction.js'
	export default {
		data() {
			return {
				friends:[],
			}
		},
		onLoad() {
			this.getFriends();
		},
		methods: {
			changeTime: function(date){
				return myfunction.dateTime(date);
			},
			getFriends: function(){
				this.friends = data.friends();
				let b=0;
				for(let i = 0; i < this.friends.length; i++){
					this.friends[i].imgurl = '../../static/test/'+this.friends[i].imgurl;
				}
			}
		}
	}
</script>

<style lang="scss">
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}
	.top-bar{
		position: fixed;
		z-index: 999;
		top: 0;
		left: 0;
		width: 100%;
		height: 88rpx;
		background: $uni-bg-color;
		border-bottom: 1px solid $uni-border-color;
		box-sizing: border-box;
		// padding-left: $uni-spacing-col-base;
		// padding-right: $uni-spacing-col-base;
		.top-bar-left{
			float: left;
			padding-left: $uni-spacing-col-base;
			image{
				margin-top: 10rpx;
				width: 68rpx;
				height: 68rpx;
				border-radius: 16rpx;
			}
		}
		.top-bar-center{
			position: absolute;
			left: 0;
			right: 0;
			top: 0;
			bottom: 0;
			text-align: center;
			margin: auto;
			.logo{
				padding-top: 19rpx;
				width: 88rpx;
				height: 42rpx;
			}
		}
		.top-bar-right{
			float: right;
			padding-right: 14rpx;
			.search{
				width: 88rpx;
				height: 88rpx;
				display: inline-block;
			}
			.add{
				width: 88rpx;
				height: 88rpx;
				display: inline-block;
			}
			image{
				padding: 18rpx 0 0 18rpx;
				width: 52rpx;
				height: 52rpx;
			}
		}
	}
	.main{
		padding-top: 104rpx;
		width: 100%;
		box-sizing: border-box;
		.friends{
			.friend-list{
				height: 96rpx;
				padding: 16rpx $uni-spacing-col-base;
				&:active{
					background-color: $uni-bg-color-grey;
				}
				.friend-list-left{
					position: relative;
					float: left;
					image{
						width: 96rpx;
						height: 96rpx;
						background-color: $uni-color-primary;
						border-radius: $uni-border-radius-base;
					}
					.tip{
						position: absolute;
						z-index: 10;
						top: 0;
						top: -6rpx;
						left: 68rpx;
						width: 36rpx;
						height: 36rpx;
						background: $uni-color-warning;
						border-radius: $uni-border-radius-circle;
						font-size: $uni-font-size-sm;
						color: $uni-text-color-inverse;
						line-height: 36rpx;
						text-align: center;
					}
				}
				.friend-list-right{
					padding-left: 128rpx;
					.top{
						height: 50rpx;
						.name{
							float: left;
							font-size: 36rpx;
							// font-family: PangFangSC-Rrgular,PingFang SC;
							font-weight: 400;
							color: $uni-text-color;
							line-height: 50rpx;
						}
						.time{
							float: right;
							font-size: $uni-font-size-sm;
							color: $uni-text-color-disable;
							line-height: 50rpx;
						}
					}
				}
				.news{
					font-size: $uni-font-size-base;
					color: $uni-text-color-grey;
					line-height: 40rpx;
					display: -webkit-box;
					-webkit-box-orient: vertical;
					-webkit-line-clamp: 1;
					overflow: hidden;
				}
			}
		}
	}
	.friend-list{
		height: 96rpx;
		padding: 16rpx $uni-spacing-col-base;
		.friend-list-left{
			position: relative;
			float: left;
			image{
				width: 96rpx;
				height: 96rpx;
				background-color: $uni-color-primary;
				border-radius: $uni-border-radius-base;
			}
			.tip{
				position: absolute;
				z-index: 10;
				top: 0;
				top: -6rpx;
				left: 68rpx;
				width: 36rpx;
				height: 36rpx;
				background: $uni-color-warning;
				border-radius: $uni-border-radius-circle;
				font-size: $uni-font-size-sm;
				color: $uni-text-color-inverse;
				line-height: 36rpx;
				text-align: center;
			}
		}
		.friend-list-right{
			padding-left: 128rpx;
			.top{
				height: 50rpx;
				.name{
					float: left;
					font-size: 36rpx;
					// font-family: PangFangSC-Rrgular,PingFang SC;
					font-weight: 400;
					color: $uni-text-color;
					line-height: 50rpx;
				}
				.time{
					float: right;
					font-size: $uni-font-size-sm;
					color: $uni-text-color-disable;
					line-height: 50rpx;
				}
			}
		}
		.news{
			font-size: $uni-font-size-base;
			color: $uni-text-color-grey;
			line-height: 40rpx;
			display: -webkit-box;
			-webkit-box-orient: vertical;
			-webkit-line-clamp: 1;
			overflow: hidden;
		}
	}
	
</style>
