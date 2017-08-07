<template>
	<div id="tickets">
		<div class="sousuo">
		<ul>
		<li>
			<p>大连</p>
			<span><i class="iconfont icon-moreunfold"></i></span>
		</li>
		<li>
			<input type="text" placeholder="影片/影院/影人 任你搜索"/>
		      </li>
		</ul>
		</div>
		<div class="xia">
		<div class="header">
			<ul>
				<router-link tag="li" to="/tickets/all" activeClass="active">全部<span>|</span></router-link>
				<router-link tag="li" to="/tickets/money" activeClass="active">价格<span>|</span></router-link>
				<router-link tag="li" to="/tickets/select" activeClass="active"><span><i class="iconfont icon-filter"  @click="openPicker"></i></span>筛选</router-link>
			</ul>
		</div>
		<router-view></router-view>
		<mt-datetime-picker ref="picker" type="date" v-model="pickerValue"></mt-datetime-picker>
		<!-- <mt-picker :slots="slots" @change="onValuesChange" class="cs"></mt-picker> -->
	</div>
</div>
</template>

<script>
import { DatetimePicker } from 'mint-ui';
	export default{
		data(){
			return{
				pickerValue:new Date("January 12,2006 22:19:35")
				// slots: [
				//        {
				//          flex: 1,
				//          values: ['2015-01', '2015-02', '2015-03', '2015-04', '2015-05', '2015-06'],
				//          className: 'slot1',
				//          textAlign: 'right'
				//        }, {
				//          divider: true,
				//          content: '-',
				//          className: 'slot2'
				//        }, {
				//          flex: 1,
				//          values: ['2015-01', '2015-02', '2015-03', '2015-04', '2015-05', '2015-06'],
				//          className: 'slot3',
				//          textAlign: 'left'
				//        }
				//      ]
			}
		},
		methods:{
			openPicker() {
			       this.$refs.picker.open();
			     },
			onValuesChange(picker, values) {
			     if (values[0] > values[1]) {
			       picker.setSlotValue(1, values[0]);
			     }
			   }
		}
	}
</script>

<style scoped lang="scss">
$ui-width: 750px;
@function px2rem($px) {
    @return $px/$ui-width*7.5rem;
}
	#tickets{
		.cs{
			background:red;
			width:1000px;
			height:1000px;
			display:block;
		}
			.sousuo{
				width: 100%;
				height:px2rem(100px);
				
				ul{
					width:375px;
					height:61px;
					padding:50px 35px;
					border-bottom: 1px solid #d8d8d8;
					display: flex;
					justify-content: space-between;
					align-items: center;
					li{
						width:40%;
						height:60px;
						line-height:60px;
						position:relative;
						p{
						    width:100%;
						    font-size:37px;

						}
						span{
							width:30px;
							display:inline-block;
							height:100%;
							position:absolute;
							margin-left:60px;
						i{
						  	width:30px;
						  	height:30px;
						  	font-size: px2rem(30px);
						  	font-weight: bold;
						  	color:#000;
						  	position:absolute;
						  	left:27px;
							top: -55px;
						 }
					}
				}
				li:nth-child(2){
					width:60%;
					height:30px;
					input{
						width:537px;
						height:57px;
						border-radius: 7px;
						position:absolute;
						left:24px;
						top:-6px;
						vertical-align: middle;
						color: #777;
						font-size: px2rem(25px);
						padding-left:5px;
					}
				}
			}	
		 }
		 .xia{
		 	background:#fff;
		 	width:100%;
		.header{
			width:100%;
			height:100px;
			ul{
				display:flex;
				justify-content:space-around;
				align-items:center;
				height:100px;
				line-height:100px;
				font-size: px2rem(33px);
				li{
					position:relative;
					span{
						display:inline-block;
						position:absolute;
						left:143px;
						color:#ccc;
					}

				}
				li:last-child{

					span{
						display:inline-block;
						position:absolute;
						left:-45px;
						color:#ccc;
						i{
							font-size: px2rem(33px);
						}
					}
				}
				.active{
					color:#1e7dd7;
					i{
						color:#1e7dd7;
					}
				}
			}
		}
	}
}
</style>