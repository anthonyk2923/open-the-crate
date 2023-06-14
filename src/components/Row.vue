<template>
    <img ref="image" src="../assets/logo.png" @load="$emit('getImageSize')" id="img" style="width:5%;">
</template>

<script>
export default {
    name: 'Row',
}
</script>
<style></style>
