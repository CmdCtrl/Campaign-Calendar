<template>
  <div id="entryForm">
    <form>
        <label>Year: </label>
        <input type="text" placeholder="ex: 1358 DR" required>
        <label>Day: </label>
        <input type="number" placeholder="##">
        <label>Month: </label>
        <input type="text" placeholder="ex: Kythorn">
        <br />
        <textarea cols="10" rows="8" placeholder="Tell your tale..."></textarea>
    </form>
  </div>
</template>

<script>
export default {
    
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

</style>