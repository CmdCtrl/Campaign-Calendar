<-- Old version of Entry.vue for reference -->
<template>
    <div class="entry-post">
        <h1>Timeline</h1>
        <div v-for="(entry, index) in entryList" :item="entry" :key="index">
            <li>
                <h2 class="noselect" @click="toggle">{{ entry.year }} {{ entry.month }} {{ entry.day }}</h2>
                <h3>{{ entry.title }}</h3>
                <p v-if="showPreview">{{ entry.sub + `...` }}</p>
                <p v-else>{{ entry.event }}</p>
                <br />
            </li>
        </div>
    </div>
</template>

<script>
export default {
    //the props are still required since data is still being passed to this component in the form of
    //entry objects. the prop maps out an entry and allows the data to be assigned to the right locations
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
    },
    data() {
        return {
            entryList: [],
            showPreview: true,
        };
    },
    //constructing the array of entries within home made the watch unnecessary, all entries are added to
    //said array before this component is used, thus the container creates a new instance with each for call.
    watch: {
        entry: function() {
            this.entryList.push(this.entry);
        }
    },
    computed: {
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
        background-clip: text;
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