<template>
    <div id="containerforside" class="bg-dark text-light p-5">
        <div id="info">
            <hr>
            <h1 class="p-2">Open The Crate</h1>
            <hr>
            <h5>A more exciting and interactive way to pick a random number!</h5>
            <span>↓</span>
            <p class='fw-lighter'>Enter a minimum and maximum number and then open a crate by clicking on one, each crate
                has a
                random number. </p>
            <span>↓</span>
        </div>
        <form>
            <div class="mb-3 left ">
                <label for="minimum" class="form-label">Minimum number:</label>
                <input type="number" class="form-control" id="minimum" value="0">
            </div>
            <div class="mb-3 left">
                <label for="maximum" class="form-label">Password:</label>
                <input type="number" class="form-control" id="number" value="100">
            </div>
            <br>
            <button type="submit" class="btn btn-primary">Submit</button>
            <span class=""></span>
        </form>
    </div>
</template>

<script>
export default {
    name: 'Sidebar'
}
</script>

<style scoped>
* {
    /* padding-left: 10%; */
    text-align: center;
}

#containerforside {
    width: 30%;
}

.left {
    text-align: left;
    padding-left: 10px;
}
</style>