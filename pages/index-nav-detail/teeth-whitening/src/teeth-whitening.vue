<template>
  <view class="teeth-whitening">
	  <!-- 搜索框 -->
	  <u-search placeholder="请输入关键字" disabled @click="search" :showAction="false"></u-search>
	  <!-- 轮播图 -->
    <swiper-image :swiperData="swiperData"></swiper-image>
    <!-- 分割线 -->
    <divider></divider>
  <!-- nav -->
    <view class="tab-bar ">
		<block v-for="item in selectList" :key="item.index">
		  <view class="tab-item" @click="changeTab(item)">
			<text :class="item.index === tabIndex ? 'is-slected' : ''">{{item.name}}</text>
		    <view class="underline" v-if="item.index === tabIndex"></view>
		  </view>
		</block>
	</view>
	

	<view class="goodsInfo p-2">
			<!-- 具体商品信息 -->
		<template v-if="tabIndex === 0">
			<view class="mb-2" v-for="(item, index) in shopData" :key="index">
				<uni-card :isFull="true"  padding="0px" @click="goGoodsDeatail">
					<view class="d-flex flex-row m-2 a-center"  >
						<view style="margin-left: -20upx;">
							<u--image :showLoading="true" :src="item.src" width="84px" height="84px"></u--image>
						</view>
					  
					  <view class="infoText flex-column ml-2">
					    <text class="font-weight font-md"  >{{ item.address }}</text>
					    <u-rate count="5" v-model="value" readonly allowHalf="true"></u-rate>
					    <text>{{ item.desc }}</text>
					    <view class="flex-row j-center a-center "></view>
					    <text style="border: #F0AD4E solid 1px; color: #E45656;" class="px-1">国家认证</text>
					    <text style="border: #F0AD4E solid 1px; color: #E45656;" class="mx-1 px-1">顶级医师</text>
					  </view>
					</view>
				</uni-card>
			</view>
		</template>
		<!-- 医生信息 -->  
		<template v-else-if="tabIndex === 1">
			<view class="mb-2" v-for="(item, index) in doctorInfo" :key="index"> 
			<uni-card :isFull="true"  padding="0px"  >
				<view class="d-flex flex-row m-2 a-center"  >
					<view style="margin-left: -20upx;">	 <u-avatar :src="item.avatar" size="60"></u-avatar></view>
			
				 <view class="doctorDesc font-md ml-2">
					 <text>
						 <text class="font-weight font-lg text-dark pr-1">{{item.name}}</text>
						 <text >{{item.level}} 从业{{item.workYear}}年
						 </text>
					 </text>
					 <view class="mb-1">
						 {{item.address}}
					 </view>
					 <view class="d-flex">
						 <block v-for="skillType in item.skill" :key="skillType">
						 <view class="border: 1px solid #6e6e6e;color: #6e6e6e;mr-1;px-1">{{skillType}}</view>
						 </block>
					
					 </view>
				 </view>
				</view>
			</uni-card>
			</view>
		</template>
	</view>

    <!--  </scroll-view> -->
  </view>
</template>
<script>
import swiperImage from '@/components/index/swiper-image.vue';
  export default {
  components:{
	  swiperImage 
  },
    data() {
      return {
		  value: 4.5,
		  tabIndex: 0,
        swiperData: [
          { img: 'https://s1.ax1x.com/2022/03/09/bWKB6S.png' },
          { img: 'https://s1.ax1x.com/2022/03/09/bWKNFI.png' },
          { img: 'https://s1.ax1x.com/2022/03/09/bWK0l8.png' }
        ],
		selectList: [
		 {
			 index: 0,
			 name: '商品'
		 },
		 {
			 index: 1,
			 name: '医生'
		 }
		],
		shopData: [
		  {
		    src: 'https://s1.ax1x.com/2022/03/09/bWK0l8.png',
		    address: '国贸口腔(国贸路def区4栋11楼)',
		    desc: '国贸路|齿科',
		    label: ['']
		  },
		  {
		    src: 'https://s1.ax1x.com/2022/03/09/bWK0l8.png',
		    address: '国兴口腔(国兴路xyz区5栋12楼)',
		    desc: '国兴路|齿科',
		    label: ['']
		  },
		  {
		    src: 'https://s1.ax1x.com/2022/03/09/bWK0l8.png',
		    address: '国兴口腔(国兴路xyz区5栋12楼)',
		    desc: '国兴路|齿科',
		    label: ['']
		  },
		  {
		    src: 'https://s1.ax1x.com/2022/03/09/bWK0l8.png',
		    address: '国兴口腔(国兴路xyz区5栋12楼)',
		    desc: '国兴路|齿科',
		    label: ['']
		  },
		  {
		    src: 'https://s1.ax1x.com/2022/03/09/bWK0l8.png',
		    address: '德韩口腔(德胜路abc区3栋10楼)',
		    desc: 'abc路|齿科',
		    label: ['']
		  }
		],
		doctorInfo: [
			{
				avatar: 'https://img0.baidu.com/it/u=105674555,346783603&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=500',
				name: '张三',
				level: '主任医生',
				workYear: 15,
				address: '海南口腔医院',
				skill: [
					'普通种植',
					'冷光美白',
					'即刻种植'
				]
			},
			{
				avatar: 'https://img0.baidu.com/it/u=105674555,346783603&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=500',
				name: '张三',
				level: '主任医生',
				workYear: 15,
				address: '海南口腔医院',
				skill: [
					'普通种植',
					'冷光美白',
					'即刻种植'
				]
			},
			{
				avatar: 'https://img0.baidu.com/it/u=105674555,346783603&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=500',
				name: '张三',
				level: '主任医生',
				workYear: 15,
				address: '海南口腔医院',
				skill: [
					'普通种植',
					'冷光美白',
					'即刻种植'
				]
			},
			{
				avatar: 'https://img2.baidu.com/it/u=3692805559,3486749732&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=538',
				name: '小明',
				level: '副主任医生',
				workYear: 10,
				address: '杭牙维信口腔',
				skill: [
					'冷光美白',
					'拔智齿',
					'即刻种植'
				]
			},
	{
		avatar: 'https://img0.baidu.com/it/u=105674555,346783603&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=500',
		name: '张三',
		level: '主任医生',
		workYear: 15,
		address: '海南口腔医院',
		skill: [
			'普通种植',
			'冷光美白',
			'即刻种植'
		]
	},
	{
		avatar: 'https://img2.baidu.com/it/u=3692805559,3486749732&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=538',
		name: '小明',
		level: '副主任医生',
		workYear: 10,
		address: '杭牙维信口腔',
		skill: [
			'冷光美白',
			'拔智齿',
			'即刻种植'
		]
	},
		]
      }
    },
    methods: {
      search(){
		  uni.navigateTo({
		  	url: '/components/search/search'
		  })
	  },
	  changeTab(item) {
		  this.tabIndex = item.index
	  },
	  goGoodsDeatail(){
		  uni.navigateTo({
		  	url: '/pages/goods-detail/goods-detail'
		  })
	  }
    }
  }
</script>

<style scoped>
.teeth-whitening >>> .u-search__content {
	margin: 20upx;
}
.tab-bar {
	display: flex;
	height: 90upx;
}
.tab-bar .tab-item {
	width: 350upx;
	height: 90upx;
    display: flex;
	flex-direction: column;
	justify-content: center;
	align-items: center;
	font-size: 40upx;
}
.is-slected {
	font-weight: 700;
}
.underline {
	height: 10upx;
	width: 90upx;
	background-color: #007AFF;
}
.goodsInfo {
	background-color: #f5f5f5;
}
</style>
