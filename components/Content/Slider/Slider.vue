<template>
<div class="slide">  
    <div class="navigation">
        <div :style="counter === index ? 'background-color: #ffffff;' : ''" v-for="(dot, index) in mainSlider" @click="changeBack(index)" :key="dot.id" class="dot"></div>
    </div>
    <div 
        v-for="slideItem in  mainSlider" 
        :key="slideItem.id" 
        :style="{ backgroundImage: 'url(' + require(  '../../../assets' + slideItem.Img ) + ')',  transform: 'translateY('+deg+'px)'} " 
        class="slider"> 
        <div class="items">
            <div class="content">
                <span v-html="slideItem.PreHeading"></span>
                <div class="mainText">
                    <h1 v-html="slideItem.Heading"></h1>
                    <span v-html="slideItem.PostHeading"></span>
                </div>
                <a :href= slideItem.Link >SHOP NOW!</a>
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
            counter: 0,    
            mainSlider: [],
            deg: 0
        }
    },
    mounted() {  
        this.mainSlider = data.SiteData.MainSlider;
        setInterval(() => this.changeBack(this.moveItems()), 3000);
    },
    methods: {   
        changeBack(id) {  
            this.counter = id;
            this.deg = -850 * id; 
        },
        moveItems() {
            this.counter < this.mainSlider.length -1 ? this.counter++ : this.counter = 0;
            return this.counter; 
        }
    }
}
</script>
<style scoped>
@import './slider.css';
</style>