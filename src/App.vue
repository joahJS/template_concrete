<template>
    <div id="wrap" class="flex flex-col">
        <HeadPrimary />

        <main id="contentView">
            <div class="mx-auto">
                <router-view></router-view>
            </div>
            <FootPrimary />
        </main>

       
    </div>
</template> <!-- Template Ends -->

<script setup>
    import HeadPrimary from './components/HeadPrimary.vue'
    import FootPrimary from './components/FootPrimary.vue'
</script> <!-- Logic Ends -->

<style lang="scss" scoped>

</style> <!-- Stylesheet Ends -->