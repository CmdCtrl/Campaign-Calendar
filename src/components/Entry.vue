<template>
    <div class="entry-post">
        <h1>Timeline</h1>
        <div class="entry" v-for="(entry, index) in entryList" :item="entry" :key="index">
            <li>
                <h2 class="noselect" @click="toggle">{{ entry.year }} {{ entry.month }} {{ entry.day }}</h2>
                <h3>{{ entry.title }}</h3>
                <p v-if="showPreview">{{ entry.sub }}</p>
                <p v-else>{{ entry.event }}</p>
            </li>
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
        },
        eventPreview: {
            subText: String,
        },  
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

h2 {
    cursor: pointer;
    &:hover {
        background-image: linear-gradient(to right, #CC2e50, #FF5858);
        background-size: 100%;
        -webkit-background-clip: text;
        -moz-background-clip: text;
        -webkit-text-fill-color: transparent; 
        -moz-text-fill-color: transparent;
    }
}

.noselect {
  -webkit-touch-callout: none; /* iOS Safari */
    -webkit-user-select: none; /* Safari */
     -khtml-user-select: none; /* Konqueror HTML */
       -moz-user-select: none; /* Old versions of Firefox */
        -ms-user-select: none; /* Internet Explorer/Edge */
            user-select: none; /* Non-prefixed version, currently
                                  supported by Chrome, Edge, Opera and Firefox */
}

</style>