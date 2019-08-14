<template>
	<div>
		<my-table ref="myTable" />

		<t-button-vue @addData="addTable" />
	</div>
</template>

<script>
import MyTable from "../../components/Tables/My-table.vue";
import tButtonVue from "../../components/button-table/t-button.vue";

export default {
	components: {
		"my-table": MyTable,
		tButtonVue
	},
	methods: {
		addTable(data) {
			this.$refs.myTable.add(data);
		}
	}
};
</script>

<style>
</style>
