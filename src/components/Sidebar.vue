<template>
    <div id="containerforside" class="bg-dark text-light p-5">
        <div id="info">
            <hr>
            <h1 class="p-2">Open The Crate</h1>
            <hr>
            <h5>A more exciting and interactive way to pick a random number!</h5>
            <span>↓</span>
            <p style="font-weight: 300;">Enter a minimum and maximum number and then open a crate by
                clicking on one, each crate
                has a
                random number!<br><strong style="font-weight: 600;">Default values: Minimum - 0, Maximum - 100</strong></p>
            <p class="even-lighter"> Please note that after clicking on a crate, its value is randomized so you
                can
                click on it again without getting the same number.</p>
            <span>↓</span>


        </div>
        <form @submit.prevent="$emit('submitForm')">
            <div class="mb-3 left ">
                <label for="minimum" class="form-label">Minimum number:</label>
                <input type="number" class="form-control" id="minimum" placeholder="0" min="0" required>
            </div>
            <div class="mb-3 left">
                <label for="maximum" class="form-label">Maximum number:</label>
                <input type="number" class="form-control" id="maximum" placeholder="100" required>
            </div>
            <div class="mb-3 left">
                <label for="size" class="form-label ">Amount of boxes:</label>
                <input type="range" class="form-range" min="4" max="10" step="1" id="size" value="8">
            </div>
            <button type="submit" class="btn btn-primary ">Submit</button>
            <span class=""></span>
        </form>
    </div>
</template>

<script>
export default {
    name: 'Sidebar',

    props: {
        randomNumber: Number
    },
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

.even-lighter {
    font-weight: 300;
    font-size: small;
}
</style>