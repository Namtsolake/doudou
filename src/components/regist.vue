<template>
	<div id="regist">
		<ul>
			<li>
				手机号：<input type="text" placeholder="请输入手机号">
			</li>
			<li>
				验证码：<input type="text" placeholder="验证码">
			</li>
			<li>
				密码：<input type="password" placeholder="6-20字母，数字，符号组成">
			</li>
			<li>
				<input type="checkbox">我已阅读并同意《豆豆网服务条款》
			</li>
			<li>
				<button>注册</button>
			</li>
			<li>
				<router-link tag="a" to="/myder" activeClass="active">请登录</router-link>
			</li>
		</ul>
							
	</div>
</template>

<script>
	export default{
		mounted(){
			console.log(333);
		}
		
	}
</script>

<style scoped lang="scss">
	#regist{
		ul{
			width:100%;
			background:#fff;
			li{
				padding:30px 30px 5px 30px;
				font-size:33px;
				input{
					width:70%;
					border:0;
					border-bottom:1px solid #ccc;
					// height:50%;
					font-size:30px;
					margin-left:25px;
				}
				button{
					background:#1e7dd7;
					border:1px solid #1e7dd7;
					color:#fff;
					width:450px;
					height:75px;
					border-radius:60px;
					font-size: 30px;
					text-align:center;
				}
			}
			li:nth-child(5){
				padding-left:124px;
				padding-bottom:30px;
			}
			li:nth-child(4){
				justify-content:center;
				font-size:30px;
				color:#333;
				text-align: center;
				input{
					width:30px;
					height:30px;
				}
			}
			li:nth-child(6){
				background:#efefef;
				font-size:30px;
				color:#333;
				a{
					color:#1e7dd7;
					font-weight:400;
				}
			}
			.active{
				color:#333;
			}
		}
	}
</style>