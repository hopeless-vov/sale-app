<template>
    <div class="content">
        <Slider />
        <div class="position">
            <NewArrival />
            <PartnersBlock />
        </div> 

    </div>
</template>

<script>
import Slider from './Slider/Slider';
import NewArrival from './NewArrival/NewArrival';
import PartnersBlock from './PartnersBlock/PartnersBlock';
export default {
    components: {
        Slider,
        NewArrival,
        PartnersBlock
    }
}
</script>
<style scoped>
@import './content.css';
</style>