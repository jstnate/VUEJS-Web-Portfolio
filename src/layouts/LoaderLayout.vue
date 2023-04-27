<template>
    <div class="preloader" id="preloader">
        <img src="@/assets/icons/logos/square_nate-logo.svg" alt="">
    </div>
</template>
<script>
export default {
    name: "LoaderLayout",
    mounted() {
        window.onload = () => {
            setTimeout(() => {
                document.getElementById("preloader").style.display = "none";
            }, 3500);
        }
    }
}
</script>
<style lang="scss" scoped>
    .preloader {
        position: fixed;
        inset: 0;
        width: 100vw;
        height: 100vh;
        background-color: #7d575d;
        z-index: 9999;
        overflow: hidden;
        display: flex;
        align-items: center;
        justify-content: center;
        animation: loaderHidding 4s;

        img {
            width: 150px;
            aspect-ratio: 1/1;
            animation: loaderAnimation 2s;
        }

        @keyframes loaderAnimation {
            0% {
                // transform: scale(.8);
                transform: rotate(0) scale(.5);
            }

            100% {
                // transform: scale(1);
                transform: rotate(720deg) scale(1);
            }
        }

        @keyframes loaderHidding {
            0% {
                opacity: 1;
            }

            50% {
                opacity: 1;
            }

            100% {
                opacity: 0;
            }
        }
    }
</style>