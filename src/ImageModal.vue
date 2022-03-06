<template>
    <div v-if="this.openImageModal" id='image-modal' class="imageModal">
        <div class="imageModal__closeContainer">
            <img @click="handleCloseModal()" class="imageModal__closeContainer__close" src="./assets/close.svg" alt="">
        </div>
        <span v-if="currentCaroselImages.length > 1" class="imageModal__position">{{imageIndex+1}}/{{currentCaroselImages.length}}</span>
        <div class="imageModal__carosel">
            <div v-if="currentCaroselImages.length > 1" class="imageModal__carosel__previousButtonContainer">
                <img @click="handlePreviousImageClick()" class="imageModal__carosel__previousButtonContainer__previousImageButton" src="./assets/chevron-right.svg" alt="">
            </div>
            <img class="imageModal__carosel__image" :src="currentCaroselImages[imageIndex]" alt="">
            <div v-if="currentCaroselImages.length > 1" class="imageModal__carosel__nextButtonContainer">
                <img @click="handleNextImageClick()" class="imageModal__carosel__nextButtonContainer__nextImageButton" src="./assets/chevron-right.svg" alt="">
            </div>
        </div>
        
    </div>
</template>

<script>
export default {
    name: 'ImageModal',
    props: [
        'openImageModal',
        'currentCaroselImages',
        'imageIndex'
    ],
    methods: {
        handleCloseModal() {
            this.$emit('viewModal', [])
        },
        handleNextImageClick(){
            this.$emit('nextImage')
        },
        handlePreviousImageClick(){
            this.$emit('prevImage')
        }
    },
}
</script>

<style>
.imageModal{
    display: flex;
    flex-direction: column;
    position: fixed;
    height: 100vh;
    width: 100vw;
    z-index: 3;
    background-color: rgba(255,255,255,0.4);
}

.imageModal__closeContainer{
    display: flex;
    width: 100%;
    align-items: center;
    justify-content: flex-end;
}

.imageModal__closeContainer__close{
    cursor: pointer;
    height: 25px;
    width: 25px;
    object-fit: contain;
    margin-right: 40px;
    margin-top: 10px;
}

.imageModal__carosel{
    display: flex;
    width: 100%;
    min-width: 300px;
    align-items: center;
    justify-content: center;
}

.imageModal__carosel__nextButtonContainer__nextImageButton{
    height: 50px;
    width: 50px;
    object-fit: contain;
    cursor: pointer;
}

.imageModal__carosel__previousButtonContainer__previousImageButton{
    height: 50px;
    width: 50px;
    object-fit: contain;
    transform: rotate(180deg);
    cursor: pointer;
}

.imageModal__carosel__previousButtonContainer{
    display: flex;
    align-self: flex-start;
    height: 100%;
    align-items: center;
    justify-content: center;
}

.imageModal__carosel__nextButtonContainer{
    display: flex;
    justify-self: flex-end;
    height: 100%;
    align-items: center;
    justify-content: center;
}

.imageModal__carosel__image{
    object-fit: contain;
    max-height: 90vh;
    max-width: 90vh;
}

.imageModal__position{
    color: #F8F0E3;
    font-size: 20px;
    font-weight: bold;
    margin-top: 10px;
}

</style>
