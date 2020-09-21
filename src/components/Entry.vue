<template>
    <div class="entry-post">
        <li>
            <h2 class="noselect" @click="toggle">{{ entry.year }} {{ entry.month }} {{ entry.day }}</h2> <button @click="deleteEntry($vnode.key)">x</button>
            <h3>{{ entry.title }}</h3>
            <p v-if="showPreview && (this.entry.event.length > 30)">{{ entry.sub }}<span>...</span> </p>
            <p v-else>{{ entry.event }}</p>
            
        </li>
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
    },
    data() {
        return {
            showPreview: true,
        };
    },
    methods: {
        toggle() {
            this.showPreview = !this.showPreview;
        },
        deleteEntry(index) {
            this.$emit('delete', index);
            console.log('ENTRY INDEX: ' + index);
        },
    }
}
</script>

<style lang="scss" scoped>

.entry-post {
  width: 65%;
  padding: 20px;
}

.entry-post p {
    font-size: 18px;
    overflow-wrap: break-word;
    white-space: pre-wrap;
}

button {
  cursor: pointer;
  background: none;
  border: none;
  outline: none;
  appearance: none;

  display: inline-block;
  padding: 2px 3px;
  background-image: linear-gradient(to right, #CC2e50, #FF5858);
  border-radius: 4px;

  color: #FFF;
  font-size: 16px;
  font-weight: 700;

  box-shadow: 1px 1px rgba(0, 0, 0, 0.4);
  transition: 0.4s ease-out;

  &:hover {
    box-shadow: 3px 3px rgba(0, 0, 0, 0.6);
  }
}

span {
    font-weight: 600;
}

h2 {
    display: inline-block;
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

@media screen and (max-width: 640px) {
    .entry-post {
        width: 100%;
    }
    button {
        padding: 4px 6px;
    }
}

</style>