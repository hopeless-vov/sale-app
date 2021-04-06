<template>
    <div :style="{ backgroundImage: 'url(' + image + ')' }" class="slider"> 
        <div class="items">
            <div class="content">
                <span v-html="PreHeading"></span>
                <div class="mainText">
                    <h1 v-html="heading"></h1>
                    <span v-html="PostHeading"></span>
                </div>
                <a :href= link >SHOP NOW!</a>
            </div>
            <div class="dots">
                <div :style="counter === index ? 'background-color: #ffffff' : ''" @click="changeBack(index)" v-for="(dot,index) in length" :key="dot.index" class="dot"> 
                </div>
            </div>
        </div>  
    </div> 
</template>


<script> 
import data from '../../../assets/siteData.json';
export default {
    data() {
        return {
            heading: '',
            link: '',
            counter: 0, 
            image: '',
            PreHeading: '',
            PostHeading: '', 
            length: 0
        }
    },
    mounted() {
        this.showInfo();
        this.length = data.SiteData.MainSlider;
    },
    methods: {  
        changeBack(id) { 
            this.counter = id
            let info = data.SiteData.MainSlider[id]
            this.heading = info.Heading;
            this.link = info.Link
            this.image = require("../../../assets"+ info.Img);
            this.PreHeading = info.PreHeading
            this.PostHeading = info.PostHeading;
        },
        showInfo() {
            let info = data.SiteData.MainSlider[0]
            this.counter = 0
            this.heading = info.Heading;
            this.link = info.Link
            this.image = require("../../../assets"+ info.Img);
            this.PreHeading = info.PreHeading
            this.PostHeading = info.PostHeading;
        }
    }
}
</script>
<style scoped>
@import './slider.css';
</style>