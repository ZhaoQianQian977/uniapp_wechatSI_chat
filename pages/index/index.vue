<!--
 * @Author: 赵倩倩 1192117761@qq.com
 * @Date: 2023-04-28 08:45:34
 * @LastEditors: 赵倩倩 1192117761@qq.com
 * @LastEditTime: 2023-04-28 16:41:55
 * @FilePath: \chatGPT\pages\index\index.vue
 * @Description: 这是默认设置,请设置`customMade`, 打开koroFileHeader查看配置 进行设置: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%AE
-->
<template>
	<view class="container">
		<view class="type-writer-content" v-for="(item,index) in list" :key="index">
		<type-writer   :uid="item.uid" :ref="`writer${item.uid}`" :contentList="item.contentList" :delaytime="item.delaytime"></type-writer>
		</view>
		<button @click="pause(0)">暂停打字</button>
		<button @click="continues(0)">继续打字</button>
		<button @click="reset(0)">重置</button>
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
					delayTime: 300,
					uid: 0
				}
			]
		};
	},
	onLoad() {
		setTimeout(() => {
			this.list.push({
				contentList: ['bbbbbbbbbbbbbbbbbbbbbbbbbbb', 'aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa'],
				delayTime: 500,
				uid: 1
			});
		}, 2000);

		setTimeout(() => {
			this.list[1].contentList = this.list[1].contentList.concat(['ccccccccccccccccccccccccccccccccccc']);
		}, 5000);
	},
	methods: {
		finish(id, status) {
			console.log(1, id, status);
		},
		pause(id, status) {
			this.$refs[`writer${id}`][0].pause();
		},
		continues(id, status) {
			this.$refs[`writer${id}`][0].continues();
		},
		reset(id, status) {
			this.$refs[`writer${id}`][0].reset();
		}
	}
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
