<template>
    <swiper v-bind="mainSliderSettings">
        <swiper-slide v-for="slide in mainSlides" :key="slide.uniqueKey" class="mainslide-container">
            <div class="mainslide-overlay">
                <h2 class="mainslide-title">{{ slide.slideTitle }}</h2>
                <p class="mainslide-subtitle">{{ slide.subText }}</p>

                <router-link v-if="slide.linkGoto !== null" :to="slide.linkGoto" class="mainslide-link">
                    {{ slide.buttonLabel }}
                </router-link>
            </div>

            <div class="mainslide-visual">
                <video v-if="slide.visType === 'video'" class="visual-source" muted autoplay loop>
                    <source :src="slide.visSrc" type="video/mp4">
                </video>

                <img v-if="slide.visType === 'image'" class="visual-source" :src="slide.visSrc !== '' ? slide.visSrc : '/images/not-exist.png'" alt="">
            </div>
        </swiper-slide>
    </swiper>
</template> <!-- Template Ends -->

<script setup>
    import { Swiper, SwiperSlide } from 'swiper/vue'
    import { Navigation, Pagination, A11y } from 'swiper'

    import 'swiper/scss'
    import 'swiper/scss/navigation'
    import 'swiper/scss/pagination'

    const mainSliderSettings = {
        modules: [ Navigation, Pagination, A11y ],
        slidesPerView: 1,
        navigation: true,
        pagination: {
            clickable: true
        },
        onSlideChange: () => {
            console.log('끼얏호우')
        }
    }

    const mainSlides = ref([
        {
            uniqueKey: 0,
            slideTitle: '세상에서 제일 튼튼한 콘크리트',
            subText: '완전 튼튼',
            buttonLabel: '바로가기',
            linkGoto: '/',
            visType: 'video',
            visSrc: '/images/video.mp4'
        },
        {
            uniqueKey: 1,
            slideTitle: '세상에서 가장 단단한 벽돌',
            subText: '이건 뭐 쌓으면 무너지질 않음',
            buttonLabel: '바로가기',
            linkGoto: '/',
            visType: 'video',
            visSrc: '/images/vodeo02.mp4'
        },
        {
            uniqueKey: 2,
            slideTitle: '세상에서 최고로 치밀한 시멘트',
            subText: '숨쉴 틈도 없음',
            buttonLabel: '바로가기',
            linkGoto: '/',
            visType: 'video',
            visSrc: '/images/vodeo03.mp4'
        },
    ])
</script> <!-- Logic Ends -->

<style lang="scss" scoped>
    .mainslide-container {
        height: 100vh;
    }

    .mainslide-overlay {
        display: flex;
        flex-flow: column nowrap;
        justify-content: center;
        align-items: center;
        gap: 25px;
        position: absolute;
        inset: 0;
        background: {
            image: radial-gradient(ellipse at center, rgba(0 0 0 / .3), transparent);
            position: center;
            size: 100%;
        }
        color: white; // temp
        isolation: isolate;
    }

    .mainslide-title {
        color: transparent;
        font-size: max(5vmax, min(40px, 5vh));
        font-weight: 900;
        -webkit-text-fill-color: transparent;
        -webkit-text-stroke-width: 2px;
        -webkit-text-stroke-color: white;
    }

    .mainslide-subtitle {
        font-size: max(2.5vmax, min(20px, 2.5vh));
        font-weight: 900;
    }

    .mainslide-link {

    }

    .mainslide-visual {
        position: absolute;
        inset: 0;
        z-index: -1;
    }

    .visual-source {
        display: block;
        width: 100%;
        height: 100%;
        object-fit: cover;
    }
</style> <!-- Stylesheet Ends -->