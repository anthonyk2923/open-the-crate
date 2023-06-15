<template>
    <img ref="image" src="../assets/logo.png" @load="$emit('getImageSize')" @click="$emit('pickNumber')" id="img"
        :class="className">
</template>

<script>
export default {
    name: 'Row',
    props: {
        className: String
    }
}
</script>
<style scoped>
img {
    cursor: pointer;

}

.two {
    width: 2%
}

.three {
    width: 3%
}

.four {
    width: 4%
}

.five {
    width: 5%
}

.six {
    width: 6%
}

.seven {
    width: 7%
}

.eight {
    width: 8%
}

.nine {
    width: 9%
}

.ten {
    width: 10%
}
</style>
