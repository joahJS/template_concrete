<template>
    <subPageHero />
    <div id="" class="web-common-inner common-main-section">
        <BreadCrumbs />
        
        <section v-if="cateGroup[getId]">
            <div>
                <img :src="cateGroup[getId].thumImg">
                <article>
                    <h1>{{cateGroup[getId].title}}</h1>
                    <article class="news-date-box">
                        <span>{{cateGroup[getId].site}}</span>
                        <span>{{cateGroup[getId].date}}</span>
                    </article>
                   
                </article>
            </div>
        </section>
        
    </div>
    <ContactUs />
</template> <!-- Template Ends -->

<script setup>
    import subPageHero from '@/components/subPageHero.vue'
    import ContactUs from '@/components/ContactUs.vue'
    import BreadCrumbs from '@/components/breadCrumb.vue'

    import { useRoute } from 'vue-router'

    const getParams = useRoute()
    const getId = parseInt(getParams.params.id)

    const cateGroup = ref([

        {
            number: '0',
            site: 'AP신문',
            title: ' 삼표, 일본보다 62% 향상된 ‘자기치유 콘크리트’ 기술 개발',
            date: '2023.03.15',
            thumImg: '/public/images/news/news02.jpg',
            linkTo: 'https://www.apnews.kr/news/articleView.html?idxno=3008791',
        },

    ])

</script> <!-- Logic Ends -->

<style lang="scss" scoped>

   
</style> <!-- Stylesheet Ends -->