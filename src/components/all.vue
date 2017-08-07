<template>
	<div id="quanbu">
		<div class="yy">
			<ul>
				<li v-for="(data,index) in looplist8" :key="data.id">
					<p>{{data.cinameName}}<span><span>￥</span>{{data.minPrice.toString().slice(0,2)}}起</span></p>
					<p>{{data.address}}</p>
					<span class="tt"></span>
					<span class="tt2"></span>
					<span class="tt3"></span>
					<span class="tt4"></span>
				</li>

			</ul>
		</div>
	</div>
</template>

<script>
import { Indicator } from 'mint-ui';
	export default{
		data(){
			return{
				looplist8:[],
			}
		},
		mounted(){
			Indicator.open({
			  text: '加载中...',
			  spinnerType: 'fading-circle'
			});
			axios.get("/Service/callback.mi/OnlineLocationCinema/OnlineCinemasByCity.api?locationId=729&t=20178416402864779").then(res=>{
				console.log(res.data);
				this.looplist8=res.data;
				Indicator.close();
				// for(var i=0;i<this.looplist8.length;i++){
				// 	var a = (this.looplist8[i].minPrice);
				// 	// console.log(a);
				// 	var b = a.toString();
				// 	var c = b.slice(0,2);
				// 	var d="￥"+c+"起"
				// 	console.log(d);
				// 	return d
				// }
					// this.looplist9=d;
					// var b = a.toString()
					// var c = b.slice(0,2);
					// console.log(c);
					
					

			})
		}
	}
</script>

<style scoped lang="scss">
	#quanbu{
		width:100%;
		.yy{
			width:100%;
			ul{
				li{
					width:100%;
					border-bottom: 1px solid #d8d8d8;
					padding: 48px 48px 20px 40px;
					position:relative;
					p:first-child{
						font-size:30px;
						font-weight: bold;
						position:relative;
						span{
							display:inline-block;
							position:absolute;
							right:27px;
							top:-7px;
							color:#f60;
							font-weight: 100;
							font-size:33px;
							span{
								display:inline-block;
								position:absolute;
								right:70px;
								top:7px;
								font-size:25px;
							}
						}
					}
					p:nth-child(2){
						padding-top:5px;
						font-size:25px;
						color:#ccc;
						white-space: wrap;
						width:70%;
					}
					span.tt{
						background:url("http://static1.mtime.cn/html5/20170731152519/images/2014/i_cine_01.png") no-repeat;
						width:57.6px;
						height:57.6px;
						display:inline-block;
						margin-top:20px;
						background-size: 45.6px;

					}
					span.tt2{
						background:url("http://static1.mtime.cn/html5/20170731152519/images/2014/is_cine_04.png") no-repeat;
						background-size: 45.6px;
						width:57.6px;
						height:57.6px;
						display:inline-block;
						margin-top:20px;

					}
					span.tt3{
						background:url("http://static1.mtime.cn/html5/20170731152519/images/2014/is_cine_02.png") no-repeat;
						background-size: 45.6px;
						width:57.6px;
						height:57.6px;
						display:inline-block;
						margin-top:20px;

					}
					span.tt4{
						background:url("http://static1.mtime.cn/html5/20170731152519/images/2014/i_cine_03.png") no-repeat;
						width:57.6px;
						height:57.6px;
						display:inline-block;
						margin-top:20px;
						background-size: 45.6px;
					}
				}
			}
		}
	}
</style>