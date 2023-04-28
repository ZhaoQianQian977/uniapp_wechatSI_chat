<template>
	<view class="container">
		<view class="type-writer-content" v-for="(item, index) in list" :key="index"><type-writer :contentList="item.contentList" :delaytime="item.delaytime"></type-writer></view>
	</view>
</template>

<script>
import typeWriter from '../../components/type-writer.vue';
export default {
	components: { typeWriter },
	data() {
		return {
			list: [
				{
					contentList: ['aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa', 'aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa'],
					delayTime: 300
				}
			]
		};
	},
	onLoad() {
		setTimeout(() => {
			this.list.push({
				contentList: ['bbbbbbbbbbbbbbbbbbbbbbbbbbb', 'aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa'],
				delayTime: 500
			});
		}, 2000);

		setTimeout(() => {
			this.list[1].contentList = this.list[1].contentList.concat(['ccccccccccccccccccccccccccccccccccc']);
		}, 5000);
	},
	methods: {}
};
</script>

<style lang="scss">
.container {
	padding: 50upx;
	.type-writer-content {
		max-width: 60vw;
		border: 1upx solid #ccc;
		white-space: pre-wrap;
		word-wrap: break-word;
		padding: 15upx 30upx;
		border-radius: 50upx;
		margin: 20upx auto;
	}
}
</style>
