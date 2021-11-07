<template>
	<section>
		<RealStateCard
			v-for="realState in realStateData"
			:key="realState.address + realState.image"
			:data="realState"
		/>
	</section>
</template>

<script>
import RealStateCard from '@/components/RealStateCard.vue';

export default {
	name: 'RealStateList',
	components: {
		RealStateCard
	},
	props: {
		realStateData: {
			type: Array,
			required: true
		}
	}
}
</script>