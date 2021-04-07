<template>
    <div class="footer">
        <div class="content">
            <div class="description">
                <span>WILDRUN</span>
                <span>{{footerInfo.Description}}</span>
            </div>
            <div class="pagesTags">
                <div v-for="item in footerItems" :key="item.id" class="navigation">
                    <span class="title">{{item.name}}</span>
                    <span style="cursor:pointer" v-for="title in item.items" :key="title.id">{{title.Title}}</span>
                </div>
            </div>
            <div class="singUp">
                <span>SING UP FOR OUR NEWSLETTER</span>
                <span>{{footerInfo.SignUpText}}</span>
                <div class="inp">
                    <input type="text" placeholder="Enter your Email">
                    <img src="@/assets/letter.png" alt="">
                </div>
                <div class="social">
                    <a v-for="social in footerInfo.Socials" :href="social.Link" :key="social.id" >
                        <img :src="require('../../assets/social/'+ social.Type + '.svg')" :alt="social.Type"> 
                    </a>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
import data from '../../assets/siteData.json'
export default {
    data() {
        return {
            footerInfo: '',
            footerItems: []
        }
    },
    mounted() {
        this.getAllInfo();
    },
    methods: {
        getAllInfo() { 
            this.footerInfo = data.SiteData.FooterBlock; 
            let info = data.SiteData.FooterBlock.PagesTags;
            info.forEach((element,index) => { 
                this.footerItems[index] = {name : element, items :[]}
            }); 
            let child = data.SiteData.Children;  
            let oneItem = Object.values(child); 
            for(let i = 1; i < oneItem.length; i++) {   
                for(let y = 0; y < this.footerItems.length; y++) {  
                        if(this.footerItems[y].name === oneItem[i].FooterTag[0]) { 
                        this.footerItems[y].items.push(oneItem[i])
                    }
                }
            }
        }
    }
}
</script>
<style scoped>
@import './footer.css';
</style>