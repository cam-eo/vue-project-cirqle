<template>
    <div id='content-card' class="contentCard">
        <div class="contentCard__contentContainer">
            <img @click="handleImagePress()" class="contentCard__contentContainer__imageInView" :src="cardData.images.length > 0 ? cardData.images[0] : require('./assets/broken-image.svg')" alt="">
            <img class="contentCard__contentContainer__imageInViewBackgroundBlur" :src="cardData.images[0]" alt="">
            <div class="contentCard__contentContainer__creatorView">
                <img class="contentCard__contentContainer__creatorView__profilePicture" :src="cardData.influencerImage || require('./assets/avatar.png')" alt="">
                <div class="contentCard__contentContainer__creatorView__textContainer">
                    <span class="contentCard__contentContainer__creatorView__textContainer__title">{{cardData.influencerName}}</span>
                    <p class="contentCard__contentContainer__creatorView__textContainer__handle">{{cardData.handle}}</p>
                </div>
            </div>
        </div>
        <span class="contentCard__dateContainer">Posted on<strong class="contentCard__dateContainer__date">{{cardData.postingDate}}</strong></span>
        <div class="contentCard__metricsContainer">
            <div :class="{'disabled': !cardData.stats.impressions}" class="contentCard__metricsContainer__container">
                <span class="contentCard__metricsContainer__container__metric">{{cardData.stats.impressions || '-'}}</span>
                <span class="contentCard__metricsContainer__container__title">IMPRESSIONS</span>
            </div>
            <div :class="{'disabled': !cardData.stats.reach}" class="contentCard__metricsContainer__container">
                <span class="contentCard__metricsContainer__container__metric">{{cardData.stats.reach || '-'}}</span>
                <span class="contentCard__metricsContainer__container__title">REACH</span>
            </div>
            <div :class="{'disabled': !cardData.stats.engagement}" class="contentCard__metricsContainer__container">
                <span class="contentCard__metricsContainer__container__metric">{{cardData.stats.engagement ? `${cardData.stats.engagement}%` : '-'}}</span>
                <span class="contentCard__metricsContainer__container__title">ENGAGEMENTS</span>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'ContentCard',
    props: [
        'cardData'
    ],
    methods: {
        handleImagePress () {
            console.log("HELLO")
            this.$emit('viewModal')
        }
    }
}
</script>

<style>
.contentCard{
    display: flex;
    align-items: center;
    flex-direction: column;
    background-color: transparent;
    margin-left: 10px;
    margin-right: 10px;
}

.contentCard__contentContainer{
    position: relative;
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
    overflow: hidden;
    background-color: black;
    max-height: 400px;
    max-width: 400px;
}

.contentCard__contentContainer__imageInView{
    z-index: 1;
    width: 80%;
    position: absolute;
    max-width: 320px;
    object-fit: contain;
    cursor: pointer;
}

.contentCard__contentContainer__imageInViewBackgroundBlur{
    opacity: 0.3;
    width: 120%;
    filter: blur(2px);
    min-height: 400px;
}

.contentCard__dateContainer{
    display: flex;
    color: #F8F0E3;
    margin-top: 12px;
    margin-bottom: 12px;
    font-weight: lighter;
    font-size: 14px;
}

.contentCard__dateContainer__date{
    margin-left: 5px;
}

.contentCard__metricsContainer{
    display: flex;
    width: 100%;
    justify-content: space-between;
    min-width: 400px;
}

.contentCard__metricsContainer__container{
    display: flex;
    flex-direction: column;
    background: #26272a;
    padding: 10px;
    width: 100px;
    border-radius: 8px;
}

.contentCard__metricsContainer__container__title{
    font-size: 12px;
    margin-top: 4px;
    color: #e6e9ec;
}

.contentCard__metricsContainer__container__metric{
    font-size: 16px;
    color: #e6e9ec;
}

.contentCard__contentContainer__creatorView{
    display: flex;
    width: 100%;
    position: absolute;
    z-index: 2;
    align-self: flex-end;
    margin-bottom: 15px;
    align-items: center;
}

.contentCard__contentContainer__creatorView__profilePicture{
    max-height: 80px;
    max-width: 80px;
    border-radius: 50px;
    object-fit: contain;
    margin-left: 15px;
    overflow: hidden;
}

.contentCard__contentContainer__creatorView__textContainer{
    display: flex;
    flex-direction: column;
    height: 100%;
    margin-left: 10px;
    background-color: rgba(150, 150, 150, 0.5);
    padding: 10px;
    border-radius: 4px;
}

.contentCard__contentContainer__creatorView__textContainer__title{
    font-weight: bold;
    color: #F8F0E3;
    text-align: left;
    font-size: 14px;
}

.contentCard__contentContainer__creatorView__textContainer__handle{
    color: #d3d3d3;
    text-align: left;
    font-size: 12px;
}

.disabled{
    opacity: 0.5;
}

</style>
