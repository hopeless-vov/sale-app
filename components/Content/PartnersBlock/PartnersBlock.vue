<template>
    <div class="partnersBlock">
        <div v-for="image in partners" :key="image.id">
            <span class="tooltiptext">
                <span>{{image.Name}}</span>
                <br>
                <span>{{image.Description}}</span>
            </span>
            <img :src="require('../../../assets/partners'+ image.Img)" alt=""> 
        </div>
    </div>
</template>

<script> 
import data from '../../../assets/siteData.json';
export default {

    data() {
        return {
            partners: [ 
            ]
        }
    },
    mounted() { 
        this.partners = data.SiteData.PartnersBlock.CompaniesList
    },
}
</script>
<style scoped>
@import './partnersBlock.css';
</style>