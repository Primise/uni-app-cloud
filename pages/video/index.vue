<template>
	<view>
		<view class="topbar">
			<view class="h86">
				<scroll-view scroll-x :show-scrollbar="false" class="scroll-view">
					<view class="rel">
						<view class="item" v-for="(item,index) in navList" :class="{active:curNav===item.id}" :key="index" @click="switchNav(item.id,index)">
							<view class="desc">
								{{item.name}}
							</view>

						</view>
					</view>
				</scroll-view>
			</view>
		</view>

	</view>
</template>

<script>
	export default {
		data() {
			return {
				navList: [{
						name: '推荐',
						id: 34571
					},
					{
						name: 'LOCK直播',
						id: 23472
					},
					{
						name: '翻唱',
						id: 33485
					},
					{
						name: '广场',
						id: 4652
					},
					{
						name: '舞蹈',
						id: 658785
					},
					{
						name: '游戏',
						id: 62689
					},
					{
						name: '现场',
						id: 7456345
					},
				],
				curNav: "",
			};
		},
		methods: {
			// 导航切换
			switchNav(id, index) {
				this.curNav = id
				this.sliderWidth = index == 1 ? 140 : 60;

				this.sliderOffset = 126 * index + (index > 1 ? 80 : 16) + (index == 0 && 16);

				this.getList(1, 1, res => {
					this.relatedVideo = res
				})
			},
		}
	}
</script>

<style lang="scss">
	.topbar {
		.h86 {
			height: 86rpx;
		}
	}

	.scroll-view {
		position: fixed;
			top: 0;
			width: 100%;
			height: 86rpx;
			white-space: nowrap;
			text-align: center;
			line-height: 86rpx;
			color: #333;
			font-weight: 600;
			border-bottom: 1rpx solid #e6e6e6;
			z-index: 10;
			background: #fff;
			.item {
				position: relative;
				display: inline-block;
				min-width: 126rpx;
				height: 86rpx;
				line-height: 86rpx;
				padding: 0 20rpx;
				&.active{
					color:#f32628;
				}
			}
	}
</style>
