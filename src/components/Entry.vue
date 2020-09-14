<template>
    <div class="entry-post">
        <h2>Timeline</h2>
        <div class="entry" v-for="(entry, index) in entryList" :item="entry" :key="index">
            <h3>{{ entry.year }} {{ entry.month }} {{ entry.day }}</h3>
            <h3>{{ entry.title }}</h3>
            <p>{{ entry.event }}</p>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        entry: {
            year: {
            type: String,
            required: true,
            },
            month: String,
            day:  Number,
            title: String,
            event: String,
        }  
    },
    data() {
        return {
            entryList: [],
        };
    },
    watch: {
        entry: function() {
            this.entryList.push(this.entry);
        }
    }
}
</script>

<style lang="scss" scoped>
.entry-post {
  width: 95%;
  padding: 15px;
}
</style>