<template>
    <div id="app">
        <ImageModal :openImageModal.sync="openImage" />
        <div class="app__innerContainer">
            <div class="app__innerContainer__rows" v-for='(itemRow, idx) in itemsInRows' :key='`${idx}__row`' >
                <ContentCard 
                    v-on:viewModal="handleSetImageModal"
                    :cardData='item' v-for='(item, idy) in itemRow' :key='`${idy}__item`'/>
            </div>
        </div>
    </div>
</template>

<script>
import ContentCard from './ContentCard'
import ImageModal from './ImageModal'
import data from './data.json'

export default {
    name: 'App',
    components: {
        ContentCard,
        ImageModal
    },
    methods: {
        handleSetImageModal() {
            console.log("HI")
        }
    },
    data() {
        return {
            openImage: false,
        }
    },
    computed: {
    itemsInRows: function () {

        const dateOptions = { year: 'numeric', month: 'long', day: 'numeric' };

        let tempItems = []
        let tempItemsRow = []
        for(let i = 0; i < data.length; i++){
            if(tempItemsRow.length < 3){

                let tempObj = data[i]
                let formattedDate = new Date(data[i].postingDate).toLocaleDateString("en-UK", dateOptions)
                tempObj.postingDate = formattedDate

                tempItemsRow.push(tempObj)
            } if(tempItemsRow.length === 3 || i === data.length-1){
                tempItems.push(tempItemsRow)
                tempItemsRow = []
            }
        }
        
      return tempItems
    },
  }
}
</script>

<style>

*{
    margin: 0;
}

#app {
    display: flex;
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    background-color: #202022;
    width: 100%;
    height: 100%;
}

.app__innerContainer{
    display: flex;
    flex-direction: column;
    width: 100%;
    align-items: center;
    margin-top: 60px;
}

.app__innerContainer__rows{
    display: flex;
    margin-bottom: 20px;
}
</style>
