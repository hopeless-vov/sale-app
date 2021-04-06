<template>
    <div class="navigation">
        <div class="logo">
            <h1>WILDRUN</h1>
        </div>
        <NavbarItems />
    </div>
</template>

<script>
import NavbarItems from './NavbarItems/NavbarItems';
export default {
    components: {
        NavbarItems
    }
}
</script>

<style scoped>
@import './navigation.css';
@import '@/assets/global.css';
</style>