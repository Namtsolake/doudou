<template>
	<div id="detail">
<!-- 		detail-- {{ $route.params.id }} -->
		<div v-if="looplist11">
			<div class="one">
				<swipe class="my-swipe">
				  <swipe-item v-for="(data,index) in looplist11.goods.imageRects" :key="data.id">
				  <img :src="data">
				  </swipe-item>
				</swipe>
				<h2>{{looplist11.goods.longGoodsName}}</h2>
				<p>￥{{looplist11.goods.marketPrice.toString().slice(0,3)}}<span>登入享受会员价</span></p>
				<p>市场价<span>￥{{looplist11.goods.maxSalePrice.toString().slice(0,3)}}</span></p>
				<p><span></span><span>{{looplist11.goods.postAgeText}}</span></p>
			</div>
			<div class="two">
				<div class="top">
					<p>评价晒单({{looplist11.goods.reviewInfo.totalCount}}人评论)</p>
					<p><span>92%</span>好评<i class="iconfont icon-more"></i></p>
				</div>
				<div class="bottom">
					<ul>
						<li v-for="(data,index) in looplist11.goods.reviewInfo.reviewInfos" :key="data.id">
						<div class="one">
							<img :src="data.headPic">
							<h5>{{data.nickName}}</h5>
						</div>
						<div class="two2">
							<p>{{data.content}}</p>
							<img :src="data.imageUrls">
						</div>
						</li>
					</ul>

				</div>
			</div>
			<div class="three">
				<ul>
					<router-link tag="li" :to="{name: 'detail1', params: { id: looplist14 }}" activeClass="active">图文详情</router-link>
					<router-link tag="li" :to="{name: 'detail', params: { id: looplist14 }}" activeClass="active">购买须知</router-link>
				</ul>
				<router-view></router-view>
			</div>
			</div>
	</div>
</template>

<script>
import { Swipe, SwipeItem } from 'vue-swipe';
import Vue from"vue";
Vue.component('swipe', Swipe);
Vue.component('swipe-item', SwipeItem);
import 'vue-swipe/dist/vue-swipe.css';
import { Indicator } from 'mint-ui';
	export default{
		data(){
			return{
				looplist11:null,
				looplist12:[],
				looplist14:""
			}
		},
		mounted(){
			// Indicator.open({
			//   text: '加载中...',
			//   spinnerType: 'fading-circle'
			// });
			console.log(this.$route.params.id);
			this.looplist14=this.$route.params.id;
			console.log(this.looplist14);
			axios.get(`/Service/callback-mall.mi/product/detail.api?goodsId=${this.$route.params.id}`).then(res=>{
				console.log(res.data);
				this.looplist11=res.data.data.productDetail;
				console.log(this.looplist11.goods.reviewInfo.reviewInfos[0].headPic)
				// this.looplist12=res.data.data.productDetail
				// Indicator.close();
			})
		}
	}
</script>

<style scoped lang="scss">
#detail{
	.one{
		width:100%;
		background:#fff;
		.my-swipe {
	  height: 614px;
	  color: #fff;
	  font-size: 30px;
	  text-align: center;
	  img{
	  	width:100%;
	  }
	}
	h2{
		font-size:35px;
		font-weight:bold;
		margin:10px;
	}
	p{	
		margin:10px;
		font-size:40px;
		color:#f60;
		font-weight: 300;
		span{
			font-size:30px;
			margin-left:40px;
		}
	}
	p:nth-last-child(2){
		margin:5px 20px;
		font-size:30px;
		color:#999;
		span{
			text-decoration:line-through;
			margin-left:0px;
		}
		
	}
	p:nth-last-child(1){
		font-size:25px;
		padding:15px 10px;
		padding-top:5px;
		span:first-child{
			background:url("http://static1.mtime.cn/html5/20170731152519/images/2014/freeshiping.png") no-repeat;
			width:32px;
			height:32px;
			display: inline-block;
			margin-left:10px;
			margin-top:5px;
		}
		span:last-child{
			margin-left:5px;
		}
	}
	}
	.two{
		width:100%;
		margin-top:30px;
		background:#fff;
		.top{
			display:flex;
			justify-content:space-between;
			padding:20px;
			border-bottom:1px solid #ccc;
			p{
				font-size:30px;
			}
			p:nth-last-child(1){
				span{
					color:#f60;
				}
				i{
					font-size:30px;
				}
			}
		}
		.bottom{
			ul{
				li{
					.one{
						padding:30px 20px;
						display:flex;
						justify-content:flex-start;
						img{
							width:76px;
							height:76px;
							border-radius:50%;
						}
						h5{
							padding-top:10px;
							font-size:30px;
							font-weight:100;
							padding-left:20px;
						}
					}
					.two2{
						padding:5px 20px;
						p{
							font-size:30px;
						}
						img{
							padding:20px 0;
							width:200px;
							height:200px;
						}
					}
				}
			}
		}
	}
	.three{
		width:100%;
		margin-top:30px;
		background:#fff;
		ul{
			display: flex;
			width:100%;
			justify-content: space-around;
			li{
				font-size:35px;
				padding:30px 0;
				boredr:1px solid #ccc;
			}
			.active{
				border-bottom:5px solid #f60;
			}
		}
	}
}
	

</style>