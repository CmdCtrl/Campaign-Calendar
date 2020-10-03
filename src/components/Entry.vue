<template>
    <div class="entry-post">
        <li> 
            <button id="opts1" ref="opts1" @click="moveEntryUp($vnode.key)">&#9650;</button>
            <button id="opts2" ref="opts2" @click="moveEntryDown($vnode.key)">&#9660;</button>
            <h2 class="noselect" @click="toggle">{{ entry.year }} {{ entry.month }} {{ entry.day }}</h2> <button id="opts3" ref="opts3" @click="deleteEntry($vnode.key)">x</button>
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
            buttonToggle: false,
        };
    },
    methods: {
        toggle() {
            this.showPreview = !this.showPreview;
            if(this.buttonToggle == false){
                this.showButtons();
            }
            if(this.buttonToggle == true){
                this.hideButtons();
            }   
            this.buttonToggle = !this.buttonToggle;
        },
        deleteEntry(index) {
            this.$emit('delete', index);
            console.log('ENTRY INDEX: ' + index);
        },
        moveEntryUp(index) {
            this.$emit('up', index);
            console.log('ENTRY INDEX: ' + index);
        },
        moveEntryDown(index) {
            this.$emit('down', index);
            console.log('ENTRY INDEX: ' + index);
        },
        showButtons() {
            this.$refs.opts1.style.display = 'inline-block';
            this.$refs.opts2.style.display = 'inline-block';
            this.$refs.opts3.style.display = 'inline-block';
        },
        hideButtons() {
            this.$refs.opts1.style.display = 'none';
            this.$refs.opts2.style.display = 'none';
            this.$refs.opts3.style.display = 'none';
        }
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

#opts1, #opts2, #opts3 {
    display: none;
}

#opts1, #opts2 {
    padding: 1px 1px;
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
    #opts1, #opts2 {
        display: inline-block;
    }
}

</style>