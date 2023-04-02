<template>
    <div class="slider">
        <ProjectCard class="slider__item slider__item-3 first-plan" data-index="3" cover="carbon_mockup.png" title="Carbon" type="Site Web" url="#" />
        <ProjectCard class="slider__item slider__item-1 third-plan" data-index="1" cover="pantheon-project_mockup.png" title="Projet Panthéon" type="Site Web" url="#" />
        <ProjectCard class="slider__item slider__item-2 second-plan" data-index="2" cover="flouflix_mockup.png" title="Flouflix" type="Site Web" url="#" />
        <ProjectCard class="slider__item slider__item-4 second-plan" data-index="4" cover="flouflix_mockup.png" title="Flouflix" type="Site Web" url="#" />
        <ProjectCard class="slider__item slider__item-5 third-plan" data-index="5" cover="pantheon-project_mockup.png" title="Projet Panthéon" type="Site Web" url="#" />
    </div>
    <div class="slider__controls">
        <button class="slider__controls__previous"><i class="fa-solid fa-chevron-left"></i> Previous</button>
        <button class="slider__controls__next">Next <i class="fa-solid fa-chevron-right"></i></button>
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

        let currentPosition = 0;

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
            });
        }

        previousButton.addEventListener('click', () => {
            currentPosition = (currentPosition - 1 + sliderItems.length) % sliderItems.length;
            updateSlider();
        });

        nextButton.addEventListener('click', () => {
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
            }

            &.second-plan {
                z-index: 1;
                opacity: .8;
                height: 300px;
                width: 380px;
                left: 50%;
                transform: translateX(-50%);

                &.slider__item-2 {
                    left: 30%;
                }

                &.slider__item-4 {
                    left: 70%;
                }
            }

            &.third-plan {
                opacity: .4;
                height: 250px;
                width: 330px;
                left: 50%;
                transform: translateX(-50%);

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