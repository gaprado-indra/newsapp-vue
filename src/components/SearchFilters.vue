<template>
    <div class="home-search-filters">
        <select>
            <option>
                Country
            </option>
        </select>
        <select>
            <option>
                Category
            </option>
        </select>
        <input type="text" placeholder="Search">
        <button>Search</button>
        <button>Clear</button>
    </div>
</template>

<script>
    export default {
        name: "SearchFilters",
    };
</script>