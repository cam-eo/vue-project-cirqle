<template>
    <div v-if="this.openImageModal" id='image-modal' class="imageModal">
        <img class="imageModal__image"  alt="">
    </div>
</template>

<script>
export default {
    name: 'ImageModal',
    props: [
        'openImageModal'
    ],
}
</script>

<style>
.imageModal{
    position: fixed;
    height: 100vh;
    width: 100vw;
    z-index: 3;
    background-color: white;
    opacity: 0.4;
}

</style>
