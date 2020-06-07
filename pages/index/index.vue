<template>
	<view class="content">
		<view class="text-area">
			<text class="title">{{ title }}</text>
		</view>
		<view>
			<input 
			class="round lines-cyan input-fatekey"
			v-model="input.fatekey"
			placeholder="输入属于你的命运征召代码"
			maxlength="16"
			/>
		</view>
		<view>
			<button
			class="cu-btn lines-cyan round lg shadow input-button"
			@tap="startfate"
			>启动命运</button>
		</view>
		<view class="cu-modal" :class="modal.startfate==true?'show':''">
			<view class="cu-dialog">
				<view class="cu-bar bg-white justify-end">
					<view class="content">命运警告</view>
					<view class="action" @tap="hidefate">
						<text class="cuIcon-close text-red"></text>
					</view>
				</view>
				<view class="padding-xl">
					确定要介入这个原本与你无关的命运吗？</br>
					你的介入将改变那个"世界"的所谓"命运"</br>
					你将通过执棋者的讲述，来了解/探索/战斗，在那个"世界"当中。</br>
				</view>
				<view class="cu-bar bg-white justify-end">
					<view class="action">
						<button class="cu-btn line-green text-green" @tap="hidefate">取消</button>
						<button class="cu-btn bg-green margin-left" @tap="hidefate">确定</button>
		
					</view>
				</view>
			</view>
		</view>
		<view style="margin-top: 650upx;">
			<button class="cu-btn lines-cyan round lg shadow" @click="chesser_login">执棋者登录</button>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			title: '命运之书',
			modal: {
				startfate: false
			},
			input: {
				fatekey: ''
			}
		};
	},
	onLoad() {
		
	},
	methods: {
		startfate: function(){
			if(this.input.fatekey != ""){
				this.modal.startfate = true;
			}
		},
		hidefate: function(){
			this.modal.startfate = false;
		},
		chesser_login: function(e){
			uni.navigateTo({
				url: "../fater/login/login"
			})
		}
	}
};
</script>

<style>
@font-face {
	font-family: ygyxsziti;
	src: url('/static/font/ygyxsziti2.0.ttf');
}

.content {
	display: flex;
	flex-direction: column;
	align-items: center;
	justify-content: stretch;
}

.text-area {
	display: flex;
	justify-content: center;
	margin-top: 250rpx;
}

.title {
	font-size: 100rpx;
	color: #000000;
	font-family: ygyxsziti;
}

.input-fatekey {
	margin-top: 50rpx;
}

.input-button {
	margin-top: 50rpx;
}
</style>
	