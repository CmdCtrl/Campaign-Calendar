<template>
  <div class="home">
    <header>
      <Banner />
    </header>
    <div class="button-container">
      <button class="new-entry" @click="entryModal = true"><span> + </span>New Entry</button>
      <transition name="fade" appear>
        <div class="modal-overlay" v-if="entryModal" @click="entryModal = false">
        </div>
      </transition>
      <transition name="slide" appear>
        <div class="modal" v-if="entryModal" >
          <newEntry @entryData="updateTimeline" />
        </div>
      </transition>
    </div>
    <div class="timeline-header">
      <h1>Timeline</h1>
    </div>
    <div class="entry-list">
      <entryContainer :entry="entry" v-for="(entry, index) in entryList" :item="entry" :key="index"  />
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import newEntry from '@/components/newEntry.vue';
import Banner from '@/components/Banner.vue';
import entryContainer from '@/components/Entry.vue';

export default {
  name: 'Home',
  
  data() {
    return {
      entryModal: false,
      entry: null,
      entryList: [],
    };
  },

  components: {
    newEntry,
    Banner,
    entryContainer,
  },

  methods: {
    updateTimeline(entryObj) {
      this.entry = entryObj;
      this.entryList.push(this.entry);
      this.entryModal = false;
    },
  }
}
</script>

<style lang="scss">

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: sans-serif;
}

header {
  position: fixed;
  width: 100%;
  top: 0;
  z-index: 98;
}

.button-container {
  justify-content: center;
  align-items: center;
  display: flex; 
  min-height: 15vh;
}

.new-entry {
  position: fixed;
  top: 200px;
  right: 550px;
  z-index: 99;

  cursor: pointer;
  background: none;
  border: none;
  outline: none;
  appearance: none;

  display: inline-block;
  padding: 14px 22px;
  background-image: linear-gradient(to right, #CC2e50, #FF5858);
  border-radius: 8px;

  color: #FFF;
  font-size: 18px;
  font-weight: 700;

  box-shadow: 3px 3px rgba(0, 0, 0, 0.4);
  transition: 0.4s ease-out;

  &:hover {
    box-shadow: 6px 6px rgba(0, 0, 0, 0.6);
  }
}

.new-entry span {
  font-size: 24px;
  font-weight: 1200;
}

.modal-overlay {
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  z-index: 98;
  background-color: rgba(0, 0, 0, 0.3);
}

.modal {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  z-index: 99;
  width: 100%;
  max-width: 400px;
  background-color: #FFF;
  border-radius: 16px;
  padding: 25px;
}

.modal h1 {
  font-size: 32px;
  color: #222;
  font-weight: 900;
  margin-bottom: 15px;
}

.modal p {
  font-size: 18px;
  font-weight: 400;
  margin-bottom: 15px;
}

.fade-enter-active, .fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
}

.slide-enter-active, .slide-leave-active {
  transition: transform 0.5s;
}
.slide-enter, .slide-leave-to {
  transform: translateY(-50%) translateX(100vw);
}  

.entry-list{
  padding: 40px;
  margin-top: 150px;
}
.timeline-header {
  background-color: #FFF;
  width:100%;
  margin: 0;
}
.timeline-header h1{
  position: fixed;
  top: 150px;
  left: 40px;
  background-color: #FFF;
  width: 100%;
  padding-top: 100px;
  z-index: 97;
}

@media screen and (max-width: 640px) {
  .new-entry {
    position: fixed;
    top: 194px;
    right: 124px;
  }
  .timeline-header h1 {
    position: fixed;
    top: 186px;
    left: 20px;
  }
}

</style>