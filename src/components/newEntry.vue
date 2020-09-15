<template>
  <div id="entryForm">
      <h2>New Timeline Entry</h2>
      <form>
          <label>Year: </label>
          <input type="text" placeholder="ex: 1358 DR" v-model="form.year" required>
          <label>Day: </label>
          <input type="number" placeholder="##" v-model="form.day">
          <label>Month: </label>
          <input type="text" placeholder="ex: Kythorn" v-model="form.month">
          <label>Title: </label>
          <input type="text" placeholder="ex: The Last Dragon-Knight" v-model="form.title">
          <br />
          <textarea cols="8" rows="5" placeholder="Tell your tale..." v-model="form.event"></textarea>
      </form>
      <br />
      <div class="submit">
          <button class="new-entry" @click="submitEntry">Submit</button>
      </div>
  </div>
</template>

<script>
export default {
    data () {
        return {
            form: {
                year: "",
                day: "",
                month: "",
                title: "",
                event: "",
                sub: "",
            }
        }
    },
    methods: {
        submitEntry: function() {
            this.form.sub = this.form.event.substring(0, 20);
            this.$emit("entryData", this.form);
        },
    }
}
</script>

<style>
#entryForm *{
    box-sizing: border-box;
}

#entryForm{
    margin: 20px auto;
    max-width: 500px;
}

label{
    display: block;
    margin: 20px 0 10px;
}

input, textarea{
    display: block;
    width: 100%;
    padding: 8px;
}

.submit {
    display: flex;
    justify-content: center;
}

</style>