<template>
    <div>
        <search-filters></search-filters>
        <data-table></data-table>
    </div>
</template>

<script>
import SearchFilters from "@/components/SearchFilters.vue";
import DataTable from "@/components/DataTable.vue"

export default {
    name: "HomeContainer",
    components: {
        SearchFilters,
        DataTable,
    },
};
</script>