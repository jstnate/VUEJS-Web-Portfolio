<template>
    <div class="slider">
        <ProjectCard class="slider__item" data-index="1" cover="carbon_mockup.png" title="Carbon" type="Site Web" url="https://carbon-le-jeu.000webhostapp.com/" />
        <ProjectCard class="slider__item" data-index="2" cover="pantheon-project_mockup.png" title="Projet Panthéon" type="Site Web" url="https://jstnate.github.io/pantheon-project/" />
        <ProjectCard class="slider__item" data-index="4" cover="vuejs-phone-app.png" title="Phone App" type="Projet VueJS" url="https://vuejs-phone-app-seven.vercel.app/#/" />
        <ProjectCard class="slider__item" data-index="5" cover="vuejs-minance-dashboard.png" title="Minance Dashboard" type="Intégration" url="https://vuejs-minance.vercel.app/#/" />
        <ProjectCard class="slider__item" data-index="3" cover="flouflix_mockup.png" title="Flouflix" type="Site Web" url="https://flouflix-devlab.000webhostapp.com/login.php" />
    </div>
    <div class="slider__controls">
        <button class="slider__controls__previous"><i class="fa-solid fa-chevron-left"></i> <span>Previous</span></button>
        <button class="slider__controls__next"><span>Next</span> <i class="fa-solid fa-chevron-right"></i></button>
    </div>
</template>
<script>
import ProjectCard from '@/components/ProjectCardComponent.vue'
export default {
    name: "SliderLayout",
    components: {
        ProjectCard
    },
    mounted() {
        const sliderItems = document.querySelectorAll('.slider__item');
        const previousButton = document.querySelector('.slider__controls__previous');
        const nextButton = document.querySelector('.slider__controls__next');
        let viewport = window.innerWidth

        let currentPosition = 0;

        window.onscroll = () => {
            responsiveAdapt()
        }

        window.addEventListener('resize', () => {
            viewport = window.innerWidth
            responsiveAdapt()
        })

        function responsiveAdapt() {
            sliderItems.forEach((item) => {
            if (viewport < 980) {
                item.classList.remove('third-plan');
            } else {
                updateSlider();
            }
        })
        }

        function updateSlider() {
            sliderItems.forEach((item, index) => {
                item.className = 'slider__item'; // Reset all classes and keep only 'slider__item'

                let offset = (index - currentPosition + sliderItems.length) % sliderItems.length;
                
                if (offset === 0) {
                    item.classList.add('first-plan');
                } else if (offset === 1 || offset === sliderItems.length - 1) {
                    item.classList.add('second-plan');
                    item.classList.add(`slider__item-${offset === 1 ? 2 : 4}`);
                } else if (offset === 2 || offset === sliderItems.length - 2) {
                    item.classList.add('third-plan');
                    item.classList.add(`slider__item-${offset === 2 ? 1 : 5}`);
                }

                if (viewport < 980) {
                    item.classList.remove('third-plan');
                }
            });
        }

        nextButton.addEventListener('click', () => {
            currentPosition = (currentPosition - 1 + sliderItems.length) % sliderItems.length;
            updateSlider();
        });

        previousButton.addEventListener('click', () => {
            currentPosition = (currentPosition + 1) % sliderItems.length;
            updateSlider();
        });

        updateSlider();
    }
}
</script>
<style lang="scss" scoped>
    .slider {
        display: flex;
        align-items: center;
        height: 400px;
        margin: 0 auto;
        width: 100%;
        position: relative;

        @media screen and (max-width: 580px) {
            height: 300px;
            max-width: 95%;
        }

        &__item {
            height: 200px;
            opacity: 0;
            position: absolute;
            width: 330px;
            z-index: 0;
            border-radius: 15px;
            transition: all .4s ease-in-out;

            &.first-plan {
                z-index: 2;
                opacity: 1;
                height: 350px;
                width: 430px;
                left: 50%;
                transform: translateX(-50%);

                @media screen and (max-width: 580px) {
                    width: 380px;
                    height: 250px;
                }

                @media screen and (max-width: 430px) {
                    width: 280px;
                    height: 200px;
                }
            }

            &.second-plan {
                z-index: 1;
                opacity: .8;
                height: 300px;
                width: 430px;
                left: 50%;
                transform: translateX(-50%);

                @media screen and (max-width: 580px) {
                    width: 280px;
                    height: 200px;
                }

                @media screen and (max-width: 430px) {
                    width: 230px;
                    height: 150px;
                }

                &.slider__item-2 {
                    left: 30%;

                    // @media screen and (max-width: 430px) {
                    //     left: 40%;
                    // }
                }

                &.slider__item-4 {
                    left: 70%;

                    // @media screen and (max-width: 430px) {
                    //     left: 60%;
                    // }
                }
            }

            &.third-plan {
                opacity: .4;
                height: 250px;
                width: 330px;
                left: 50%;
                transform: translateX(-50%);

                @media screen and (max-width: 580px) {
                    width: 280px;
                    height: 200px;
                }

                @media screen and (max-width: 430px) {
                    width: 230px;
                    height: 150px;
                }

                &.slider__item-1 {
                    left: 15%;
                }

                &.slider__item-5 {
                    left: 85%;
                }
            }
        }

        &__controls {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 50px;
            position: relative;

            button {
                position: relative;
                font-family: 'Josefin Sans', sans-serif;
                font-size: 24px;
                display: flex;
                align-items: center;
                justify-content: center;
                gap: 15px;
                width: 200px;
                padding: .8rem 3rem;
                cursor: pointer;
                background-color: #C5AA86;
                border: none;
                color: #F9F9F9;
                z-index: 1;

                @media screen and (max-width: 450px) {
                    width: 100px;
                }

                span {
                    margin-top: 3px;

                    @media screen and (max-width: 450px) {
                        display: none;
                    }
                }

                &:hover {
                    background-color: #7D575D;
                }
            }

            &__next {
                box-shadow: -5px 5px #7d575d;
            
                &:hover {
                    transform: translateX(3px) translateY(-3px);
                    box-shadow: -8px 8px #C5AA86;
                }
            } 

            &__previous {
                box-shadow: 5px 5px #7d575d;
            
                &:hover {
                    transform: translateX(-3px) translateY(-3px);
                    box-shadow: 8px 8px #C5AA86;
                }
            } 

        }
    }
</style>