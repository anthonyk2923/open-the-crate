<template>
    <Row v-for="box in Number(row_length)" :key="box" @getImageSize="$emit('getImageSize')" row_length="row_length" />
</template>

<script>
import Row from "./Row"

export default {
    name: 'Rows',
    components: {
        Row
    },
    props: {
        row_length: Number,

    }
}
</script>

<style></style>