<template>
	<view class="content">
		<!-- 今日能量瓶 -->
		<view class="bottle_box">
			<!-- 标题 -->
			<image class="bottle_title"
				src="" mode="">
			</image>
			<!-- 能量类型 -->
			<view class="energy_box">
				<!-- 根据energy_item:nth-child(n) 来调整能量类型盒子的位置-->
				<view class="energy_item" v-for="(item, index) in arrEnergyList" :key="index">
					<!-- 根据index来给不同盒子不同的动画 -->
					<view :class="{
						'float': true,
						'float0': index === 0,
						'float1': index === 1,
						'float2': index === 2,
						'float3': index === 3,
						'float4': index === 4,
						'float5': index === 5,
						'float6': index === 6,
					}">
						<image class="energy_img energy_img_green" :src="item.img"></image>
						<view class="energy_info">
							{{item.name}}
						</view>
						<view class="energy_info">
							+{{item.num}}{{item.unit}}
						</view>
					</view>
				</view>
			</view>
			<!-- 波浪 -->
			<view class="wave_box wave_animation">
				<!-- 这里有四张静态波浪图，它们是如何实现四条波浪上下摆动的动画呢？ -->
				<!-- 这里拿一张波浪图来举例解释实现波浪动画的思路： -->
				<!-- 波浪的上下摇摆实际上是通过图片的左右移动实现的，因此我们只需写一个实现波浪图从右(左)到左(右)移动的动画就行，
				 但是在实现循环移动的动画中会存在一个问题，波浪图向左移动后，将移出屏幕边界，并且右侧会空出来，因此我们在盒子内
				 放两张相同的波浪图，一张初始位置在屏幕内，一张在屏幕右侧，当第一张向左移动时，第二张紧跟着一起移动实现弥补原本
				 的空出来的位置，-->
				<div class="wave_imgs wave_imgs1">
					<!-- 由于这张图的高度是其它图的一半不到，为了提高此图的宽度，因此使用保持宽高比不变，根据宽度来改变图片高度的模式，
					在wava_imgs1中将宽度放大两倍，高度自然也就变为原先的两倍 -->
					<image class="wave_bg" src="https://pro-core.babycdn.com/2022/03/rjm/xcx/dev/image/index/wave_1.png"
						mode="widthFix">
					</image>
					<image class="wave_bg" src="https://pro-core.babycdn.com/2022/03/rjm/xcx/dev/image/index/wave_1.png"
						mode="widthFix">
					</image>
				</div>
				<div class="wave_imgs">
					<image class="wave_bg" src="https://pro-core.babycdn.com/2022/03/rjm/xcx/dev/image/index/wave_2.png"
						mode="widthFix"></image>
					<image class="wave_bg" src="https://pro-core.babycdn.com/2022/03/rjm/xcx/dev/image/index/wave_2.png"
						mode="widthFix"></image>
				</div>
				<div class="wave_imgs">
					<image class="wave_bg" src="https://pro-core.babycdn.com/2022/03/rjm/xcx/dev/image/index/wave_3.png"
						mode="widthFix"></image>
					<image class="wave_bg" src="https://pro-core.babycdn.com/2022/03/rjm/xcx/dev/image/index/wave_3.png"
						mode="widthFix"></image>
				</div>
				<div class="wave_imgs">
					<image class="wave_bg" src="https://pro-core.babycdn.com/2022/03/rjm/xcx/dev/image/index/wave_4.png"
						mode="widthFix"></image>
					<image class="wave_bg" src="https://pro-core.babycdn.com/2022/03/rjm/xcx/dev/image/index/wave_4.png"
						mode="widthFix"></image>
				</div>

				<!-- 上升的气泡 -->
				<view class="bubble_box">
					<span class="bubble_item"></span>
					<span class="bubble_item"></span>
					<span class="bubble_item"></span>
					<span class="bubble_item"></span>
					<span class="bubble_item"></span>
					<span class="bubble_item"></span>
					<span class="bubble_item"></span>
					<span class="bubble_item"></span>
					<span class="bubble_item"></span>
				</view>
			</view>
		</view>
		<!-- 本周热销 -->
		<view class="hot_sale_box">
			<image class="hot_sale_title"
				src="" mode="">
			</image>
			<!-- 气泡 -->
			<!-- 此气泡动画实现原理: -->
			<!-- 先写一个气泡水平方向向右移动、垂直方向先下后上、气泡宽高从0变大、透明度在50%时从1变为0的动画 -->
			<!-- 再复制5个相同的气泡，给每个气泡不同的动画延时animation-delay，但是每个气泡之间的延时时长必须相同。 -->
			<view class="title_bubble">
				<view class="bubble_item"></view>
				<view class="bubble_item"></view>
				<view class="bubble_item"></view>
				<view class="bubble_item"></view>
				<view class="bubble_item"></view>
				<view class="bubble_item"></view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				nBottleValue: 0, //能量瓶百分比值
				//今日能量
				arrEnergyList: [{
					name: '名字1',
					num: 0,
					img: '',
					unit: 'ug'
				}, {
					name: '名字1B6',
					num: 0,
					img: '',
					unit: 'mg'
				}, {
					name: '名字2',
					num: 0,
					img: '',
					unit: 'mg'
				}, {
					name: '名字12',
					num: 0,
					img: '',
					unit: 'mg'
				}, {
					name: '名字11',
					num: 0,
					img: '',
					unit: 'mg'
				}, {
					name: '名字98',
					num: 0,
					img: '',
					unit: 'mg'
				}, {
					name: '名字02',
					num: 0,
					img: '',
					unit: 'mg'
				}],
			}
		},
	}
</script>

<style lang="less">
	.content {
		background-color: #f4f4f4;
		height: 100vh;
		width: 100vw;
		box-sizing: border-box;
		padding: 24rpx;

		.bottle_box {
			width: 702rpx;
			height: 632rpx;
			background: linear-gradient(195deg, #FFFFFF 0%, #F7F6ED 100%);
			box-shadow: 0 8px 80px 0 rgba(0, 0, 0, 0.1);
			border-radius: 20rpx;
			margin: 15rpx auto 36rpx;
			position: relative;
			padding-top: 32rpx;

			display: flex;
			flex-direction: column;
			justify-content: space-between;
			overflow: hidden;

			.bottle_box_bubble {
				position: absolute;
				top: 0;
				right: 0;
				width: 114rpx;
				height: 112rpx;
			}

			.bottle_title {
				width: 214rpx;
				height: 42rpx;
				margin-left: 24rpx;
			}

			.ask_icon {
				position: absolute;
				top: 12rpx;
				right: 12rpx;
				z-index: 10;
				width: 36rpx;
				height: 36rpx;
			}

			.energy_box {
				width: 100%;
				height: 282rpx;
				position: relative;

				.float {
					width: 100%;
					position: absolute;
					top: 0;
					left: 0;
					animation-timing-function: linear;
					animation-iteration-count: infinite;
				}

				.float0 {
					animation-name: float0;
					animation-duration: 3s;
				}

				.float1 {
					animation-name: float1;
					animation-duration: 6s;
				}

				.float2 {
					animation-name: float2;
					animation-duration: 3.6s;
				}

				.float3 {
					animation-name: float3;
					animation-duration: 3s;
				}

				.float4 {
					animation-name: float4;
					animation-duration: 6s;
				}

				.float5 {
					animation-name: float5;
					animation-duration: 3.6s;
				}

				.float6 {
					animation-name: float6;
					animation-duration: 6s;
				}

				.energy_item {
					position: absolute;
					z-index: 10;
					width: 20%;
					height: 50%;
					min-width: 20%;

					.energy_img {
						display: block;
						width: 60rpx;
						height: 60rpx;
						margin: 0 auto 10rpx;
					}

					.energy_img_green {
						filter: grayscale(100%);
					}

					.energy_info {
						text-align: center;
						font-size: 20rpx;
						font-family: PingFangSC-Regular, PingFang SC;
						font-weight: 400;
						color: #bbd3c4;
						line-height: 32rpx;
					}
				}

				.energy_item:nth-child(1) {
					left: 4%;
				}

				.energy_item:nth-child(2) {
					left: 18%;
				}

				.energy_item:nth-child(3) {
					left: 30%;
				}

				.energy_item:nth-child(4) {
					left: 44%;
				}

				.energy_item:nth-child(5) {
					left: 52%;
				}

				.energy_item:nth-child(6) {
					left: 64%;
				}

				.energy_item:nth-child(7) {
					left: 78%;
				}
			}

			.wave_box {
				width: 100%;
				height: 236rpx;
				padding-top: 40rpx;
				position: relative;
				display: flex;
				align-items: center;

				.wave_imgs {
					width: 100%;
					height: 100%;
					position: absolute;
					left: 0;
					bottom: 0;
					z-index: 1;

					.wave_bg {
						display: block;
						width: 100%;
						min-width: 100%;
						height: 100%;
						margin: 0;
						padding: 0;
						position: absolute;
						bottom: 0;
					}

					.wave_bg:nth-child(1) {
						left: 0;
						transition: left 0.2s;
					}

					.wave_bg:nth-child(2) {
						left: 100%;
						transition: left 0.2s;
					}


				}

				.wave_bottle {
					z-index: 10;
					display: block;
					width: 38rpx;
					height: 116rpx;
					margin-left: 240rpx;

					transition: transform 1s;
					transform: scale3d(1, 1, 1);
				}

				.wave_bottle_animation {
					transition: transform 3s;
					transform: scale3d(1.6, 1.6, 1.6);
				}

				.wave_info {
					z-index: 10;
					margin-left: 16rpx;
					text-align: center;

				}

				.wave_num {
					font-size: 60rpx;
					font-family: Helvetica;
					color: white;
					line-height: 72rpx;
					text-shadow: 6rpx 6rpx 0px rgba(0, 0, 0, 0.23);
					margin-top: 10rpx;
				}

				.wave_tips {
					font-size: 24rpx;
					font-family: PingFangSC-Regular, PingFang SC;
					font-weight: 400;
					color: yellow;
					line-height: 34rpx;

				}

				.wave_imgs1 {
					width: 200%;
				}
			}

			.wave_animation {
				.wave_imgs {
					.wave_bg:nth-child(1) {
						animation-name: wave_animation;
						animation-timing-function: linear;
						animation-iteration-count: infinite;
					}

					.wave_bg:nth-child(2) {
						animation-name: wave_animation2;
						animation-timing-function: linear;
						animation-iteration-count: infinite;
					}
				}

				.wave_imgs:nth-child(1) {
					.wave_bg {
						animation-duration: 12s;
					}

					.wave_bg:nth-child(2) {
						animation-name: wave_animation3;
					}
				}

				.wave_imgs:nth-child(2) {
					.wave_bg {
						animation-duration: 18s;
					}
				}

				.wave_imgs:nth-child(3) {
					.wave_bg {
						animation-duration: 15s;
					}
				}

				.wave_imgs:nth-child(4) {
					.wave_bg {
						animation-duration: 18s;
					}
				}
			}

			.bubble_box {
				width: 100%;
				height: 100%;
				position: absolute;
				left: 0;
				bottom: 0;
				z-index: 8;

				.bubble_item {
					display: block;
					border-radius: 50%;
					background: rgba(204, 204, 204, 0.6);
					position: absolute;
					bottom: 0;
				}

				.bubble_item:nth-child(1) {
					width: 30rpx;
					height: 30rpx;
					left: 10%;
					animation: rise 3s infinite linear;
				}

				.bubble_item:nth-child(2) {
					width: 12rpx;
					height: 12rpx;
					left: 15%;
					animation: rise 1.6s infinite linear;
				}

				.bubble_item:nth-child(3) {
					width: 40rpx;
					height: 40rpx;
					left: 28%;
					animation: rise 4s infinite linear;
				}

				.bubble_item:nth-child(4) {
					width: 24rpx;
					height: 24rpx;
					left: 35%;
					animation: rise 2.8s infinite linear;
				}

				.bubble_item:nth-child(5) {
					width: 28rpx;
					height: 28rpx;
					left: 44%;
					animation: rise 3.4s infinite linear;
				}

				.bubble_item:nth-child(6) {
					width: 16rpx;
					height: 16rpx;
					left: 52%;
					animation: rise 2s infinite linear;
				}

				.bubble_item:nth-child(7) {
					width: 24rpx;
					height: 24rpx;
					left: 63%;
					animation: rise 2.4s infinite linear;
				}

				.bubble_item:nth-child(8) {
					width: 30rpx;
					height: 30rpx;
					left: 75%;
					animation: rise 3s infinite linear;
				}

				.bubble_item:nth-child(9) {
					width: 40rpx;
					height: 40rpx;
					left: 88%;
					animation: rise 5s infinite linear;
				}
			}

		}

		.hot_sale_box {
			width: 702rpx;
			background: #fff;
			border-radius: 20rpx;
			margin: 60rpx auto 0;
			position: relative;
			overflow: hidden;

			.hot_sale_title {
				display: block;
				width: 6rpx;
				height: 42rpx;
				margin: 28rpx auto 24rpx 28rpx;
			}

			.title_bubble {
				width: 436rpx;
				height: 100rpx;
				position: absolute;
				top: 0;
				left: 0;
				z-index: 999;

				.bubble_item {
					width: 0;
					height: 0;
					border-radius: 50%;
					background-color: #268159;
					position: absolute;
					left: 0;
					top: 50%;
					transform: translateY(-50%);
					animation-name: bubble_hor;
					animation-duration: 9s;
					animation-timing-function: linear;
					animation-delay: 0;
					animation-iteration-count: infinite;
				}

				.bubble_item:nth-child(2) {
					animation-delay: 1.5s;
				}

				.bubble_item:nth-child(3) {
					animation-delay: 3s;
				}

				.bubble_item:nth-child(4) {
					animation-delay: 4.5s;
				}

				.bubble_item:nth-child(5) {
					animation-delay: 6s;
				}

				.bubble_item:nth-child(6) {
					animation-delay: 7.5s;
				}
			}
		}
	}

	@keyframes float0 {
		0% {
			top: 10rpx;
		}

		50% {
			top: 30rpx
		}

		100% {
			top: 10rpx;
		}
	}

	@keyframes float1 {
		0% {
			top: 156rpx;
		}

		50% {
			top: 136rpx
		}

		100% {
			top: 156rpx;
		}
	}

	@keyframes float2 {
		0% {
			top: 12rpx;
		}

		50% {
			top: 32rpx
		}

		100% {
			top: 12rpx;
		}
	}

	@keyframes float3 {
		0% {
			top: 136rpx;
		}

		50% {
			top: 116rpx
		}

		100% {
			top: 136rpx;
		}
	}

	@keyframes float4 {
		0% {
			top: -40rpx;
		}

		50% {
			top: -20rpx;
		}

		100% {
			top: -40rpx;
		}
	}

	@keyframes float5 {
		0% {
			top: 146rpx;
		}

		50% {
			top: 126rpx;
		}

		100% {
			top: 146rpx;
		}
	}

	@keyframes float6 {
		0% {
			top: 66rpx;
		}

		50% {
			top: 46rpx;
		}

		100% {
			top: 66rpx;
		}
	}

	@keyframes wave_animation {
		0% {
			left: 0;
		}

		100% {
			left: -100%;
		}
	}

	@keyframes wave_animation2 {
		0% {
			left: 100%;
		}

		100% {
			left: 0;
		}
	}

	@keyframes wave_animation3 {
		0% {
			left: calc(100% - 1rpx);
		}

		100% {
			left: -1rpx;
		}
	}

	@keyframes rise {
		0% {
			bottom: -40rpx;
			opacity: 1;
		}

		75% {
			opacity: 1;
		}

		100% {
			bottom: 100%;
			opacity: 0;
		}
	}

	@keyframes bubble_hor {
		10% {
			width: 0rpx;
			height: 0rpx;
			top: calc(50% + 0rpx);
			opacity: 1;
		}

		20% {
			top: calc(50% + 10rpx);
		}

		30% {

			top: calc(50% + 20rpx);
			opacity: 1;
		}

		40% {
			width: 20rpx;
			height: 20rpx;
			top: calc(50% + 10rpx);
			opacity: 0.9;
		}

		50% {
			top: calc(50% + 0rpx);
			opacity: 0.8;
		}

		60% {
			width: 40rpx;
			height: 40rpx;
			top: calc(50% - 10rpx);
			opacity: 0.7;
		}

		;

		70% {
			top: calc(50% - 20rpx);
			opacity: 0.5;
		}

		80% {
			top: calc(50% - 10rpx);
			opacity: 0.3;
		}

		90% {
			top: calc(50% - 0rpx);
			opacity: 0.1;
		}

		100% {
			width: 60rpx;
			height: 60rpx;
			left: 100%;
			top: calc(50% + 10rpx);
			opacity: 0;
		}
	}
</style>