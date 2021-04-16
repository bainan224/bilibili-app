<template>
	<view>
		<mSearch @search="search($event,0)"></mSearch>
	</view>
</template>

<script>
	import mSearch from '@/components/mehaotian-search/mehaotian-search.vue';
	export default {
		components: {
			mSearch
		},
		data() {
			return {
				val0: '',
				placeholder:'动态占位内容'
			}
		},
		methods: {
			search(e, val) {
			            console.log(e, val);
			            this['val'+val] = e;
			    },
		}
	}
</script>

<style>

</style>
