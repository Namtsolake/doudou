<template>
	<div id="myder">
		<ul>
			<li>
				<i class="iconfont icon-account"></i>
				<input type="text" placeholder="手机号">
			</li>
			<li>
				<i class="confont icon-box"></i>
				<input type="password" placeholder="密码">
			</li>
			<li>
				<button>登录</button>
			</li>
			<li>
				<router-link tag="a" to="/regist" activeClass="active">免费注册</router-link>
				<span>找回密码</span>
			</li>
		</ul>
	</div>
</template>

<script>
	export default{
		
	}
</script>

<style scoped lang="scss">
	#myder{
		ul{
			width:100%;
			background:#fff;
			li{
				padding:30px 30px 5px 30px;
				i{
					font-size:50px;
					padding-left:30px;
				}
				input{
					width:70%;
					border:0;
					border-bottom:1px solid #ccc;
					// height:50%;
					font-size:40px;
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
			li:nth-child(3){
				padding-left:124px;
				padding-bottom:30px;
			}
			li:nth-child(4){
				display:flex;
				justify-content:space-around;
				background:#efefef;
				font-size:30px;
				color:#333;
				a{
					color:#1e7dd7;
					font-weight:400;
				}
			}
		}
	}
</style>