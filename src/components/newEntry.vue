<template>
  <div id="entryForm">
    <form>
        <label>Year: </label>
        <input type="text" placeholder="ex: 1358 DR" v-model="form.year" required>
        <label>Day: </label>
        <input type="number" placeholder="##" v-model="form.day">
        <label>Month: </label>
        <input type="text" placeholder="ex: Kythorn" v-model="form.month">
        <br />
        <textarea cols="10" rows="8" placeholder="Tell your tale..." v-model="form.event"></textarea>
    </form>
    <br />
    <div class="submit">
        <button class="new-entry" @Click="entryModal = false">Submit</button>
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
                event: "",
            }
        }
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