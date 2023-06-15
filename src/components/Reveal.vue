<template>
    <div class="pt-2">

        <div align=center class="outer-clicked">
            <div class="clicked shadow-lg p-3 bg-white rounded">
                <h1 class="text-dark">{{ randomNumber }}</h1>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Reveal',
    props: {
        randomNumber: Number
    }

}
</script>

<style scoped>
.clicked {
    border: 0.5rem outset rgb(0, 0, 0);
    border-radius: 12px;
    font: bold 1rem sans-serif;
    outline-offset: 0.5rem;
    width: 80%;
    text-align: center;
    margin: 0;
}

.outer-clicked {
    margin: 0;
    width: 30%;
}
</style>