<template>
    <Row v-for="box in row_length" :key="box" @getImageSize="$emit('getImageSize')" @pickNumber="$emit('pickNumber')"
        row_length="row_length" :className="className" />
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
        className: String,

    }
}
</script>

<style></style>