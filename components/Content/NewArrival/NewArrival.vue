<template>
    <div class="newArrival">
        <span>NEW ARRIVAL</span>
        <div class="arrivalContent">
            <div class="man">
                <span>{{arrivalBlock.title}}</span>
                <h1>{{arrivalBlock.text}}</h1>
                <a :href="arrivalBlock.link">{{arrivalBlock.buttonText}}</a>
            </div>
            <div class="shoesItems">
                <div v-show="Number(product.ShowOnMain)" :style="{order: product.Order }" v-for="product in products" :key="product.id" class="item">
                    <img class="contentico" :src="require('../../../assets/Shoes'+product.Image)" alt="">
                    <span>{{product.Type}}</span>
                    <span class="price">{{product.Price}}</span>
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
            arrivalBlock: {
                title:'',
                text: '',
                buttonText: '',
                link: '',
                products: []
            }

        }
    },
    mounted() {
        this.getArrivalInfo();
        this.getProducts(); 
    },
    methods: {
        getArrivalInfo() { 
            let info = data.SiteData.ArrivalBlock;
            this.arrivalBlock.title = info.Title;
            this.arrivalBlock.text = info.Text;
            this.arrivalBlock.buttonText = info.ButtonText;
            this.arrivalBlock.link = info.Link;
        },
        getProducts() {
            let item = data.SiteData.Children.Products.Children;
            this.products = Object.values(item); 
        }
    }
}
</script>
<style scoped>
@import './newArrival.css';
</style>