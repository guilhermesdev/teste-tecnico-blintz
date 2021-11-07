<template>
	<section>
		<RealStateCard
			v-for="realState in realStateList"
			:key="realState.address + realState.image"
			:data="realState"
		/>
	</section>
</template>

<script>
import realStateList from '@/data/realState';
import RealStateCard from '@/components/RealStateCard.vue';

export default {
	name: 'RealStateList',
	components: {
		RealStateCard
	},
	data() {
		return {
			realStateList
		}
	}
}
</script>