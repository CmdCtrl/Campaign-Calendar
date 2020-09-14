<template>
    <div class="entry-post">
        <h1>Timeline</h1>
        <div class="entry" v-for="(entry, index) in entryList" :item="entry" :key="index">
            <h2 @click="toggle">{{ entry.year }} {{ entry.month }} {{ entry.day }}</h2>
            <h3>{{ entry.title }}</h3>
            <p v-if="showPreview">{{ preview }}</p>
            <p v-else>{{ entry.event }}</p>
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
            showPreview: true,
        };
    },
    watch: {
        entry: function() {
            this.entryList.push(this.entry);
        }
    },
    computed: {
        preview() {
            const full = this.entry.event;
            const preview = full.substring(0, 20);
            return `${preview}...`;
        }
    },
    methods: {
        toggle() {
            this.showPreview = !this.showPreview;
        },
    }
}
</script>

<style lang="scss" scoped>
.entry-post {
  width: 95%;
  padding: 15px;
}
</style>