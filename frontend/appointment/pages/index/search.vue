<template>
	<view>
		<cu-custom bgColor="bg-gradual-blue" :isBack="true"><block slot="backText">返回</block><block slot="content">预约查询</block></cu-custom>
		<view class="cu-bar search bg-white">
			<view class="search-form round">
				<text class="cuIcon-search"></text>
				<input v-model="telephone" :adjust-position="false" type="text" placeholder="请输入手机号查询中签结果" confirm-type="search"></input>
			</view>
			<view class="action">
				<button class="cu-btn bg-green shadow-blur round" @click="search">搜索</button>
			</view>
		</view>
		<view v-if="isDraw">
			<view class="flex solid-bottom padding justify-center">
				<vue-qr v-bind:text="this.data" :size="300"></vue-qr>
			</view>
			<view class="flex-sub text-center">
				<view class="solid-bottom text-xl padding">
					<text class="text-black text-bold">您已中签，凭二维码到指定药房购买口罩！</text>
				</view>
			</view>
			<button class="cu-btn bg-red margin-tb-sm lg">保存到相册</button>
		</view>
	</view>
</template>

<script>
	import vueQr from 'vue-qr'
	export default {
		data() {
			return {
				telephone: '',
				isDraw: false,
				data: {}
			}
		},
		components: {
			vueQr
		},
		methods: {
			search() {
				this.isDraw = true;
				this.data = this.telephone;
			}
		}
	}
</script>

<style>

</style>
