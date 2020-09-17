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
          <button class="submit-button" @click="submitEntry">Submit</button>
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
            this.form.sub = this.form.event.substring(0, 30);
            this.$emit("entryData", this.form);
        },
    }
}
</script>

<style lang="scss">
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

.submit-button {
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

</style>