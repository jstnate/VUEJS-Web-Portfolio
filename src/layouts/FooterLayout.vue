<template>
    <section class="footer">
        <div class="footer__div footer__me">
            <div>
                <span>Nathan LEFETEY</span>
                <span>Web Portfolio</span>
            </div>
            <img src="@/assets/icons/logos/square_white_nate-logo.png" alt="">
        </div>
        <div class="footer__div footer__infos">
            <span>92000, Nanterre</span>
            <div>
                <span>(+33)6 37 91 22 42</span>
                <span>lefetey.nathan@gmail.com</span>
            </div>
        </div>
        <div class="footer__div footer__anchor">
            <div class="footer__anchor__content">
                <div>
                    <h3>Liens Utiles</h3>
                    <a href="#about">A propos</a>
                    <a href="#my-services">Services</a>
                    <a href="#my-skills">Mes Compétences</a>
                    <a href="#my-projects">Mes Projets</a>
                </div>

                <div>
                    <h3>Réseaux</h3>
                    <a href="https://github.com/jstnate">Github</a>
                    <a href="https://www.linkedin.com/in/nathanlefetey/">Linkedin</a>
                </div>
            </div>
            <span>&copy; 2023 Nathan LEFETEY, Tout droits réservés</span>
        </div>
        <div class="footer__div footer__go-top">
            <a href="#about"><i class="fa-solid fa-arrow-up"></i></a>
        </div>
    </section>
</template>
<script>
export default {
    name: 'FooterLayout',
}
</script>
<style lang="scss" scoped>
    .footer {
        background-color: #C5AA86;
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding: 6rem;
        font-size: 16px;
        height: 50vh;
        font-family: 'Josefin Sans', sans-serif;
        color: #fff;

        @media screen and (max-width: 1100px) {
            height: auto;
            flex-direction: column;
            gap: 50px;
        }

        @media screen and (max-width: 650px) {
            padding: 6rem 1rem;
        }

        &__div {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100%;
            align-items: flex-start;
            justify-content: space-between;
        }

        &__me {
            width: calc(100% / 5);

            @media screen and (max-width: 1100px) {
                width: 80%;
                flex-direction: row;
                align-items: center;
            }

            @media screen and (max-width: 450px) {
                flex-direction: column;
                align-items: flex-start;
                gap: 25px;
            }

            div {
                display: flex;
                flex-direction: column;
                align-items: flex-start;
                justify-content: center;
                span {
                    font-size: 24px;
                    font-weight: 900;
                }
            }

            img {
                width: 150px;
                margin-top: 2rem;
            }
        }

        &__infos {
            width: calc(100% / 5);
            align-items: flex-start;
            justify-content: space-between;
            height: 100%;

            @media screen and (max-width: 1100px) {
                width: 80%;
                flex-direction: row;
                align-items: center;
            }

            @media screen and (max-width: 450px) {
                flex-direction: column;
                align-items: flex-start;
                gap: 25px;
            }

            div {
                display: flex;
                flex-direction: column;
                align-items: flex-start;

                span {
                    line-height: 1.5rem;
                }
            }
        }

        &__anchor {
            width: calc(2 * (100% / 5));

            @media screen and (max-width: 1100px) {
                width: 80%;
                display: flex;
                flex-direction: column;
                align-items: center;
            }
            
            &__content {
                display: flex;
                align-items: flex-start;
                width: 100%;

                @media screen and (max-width: 1100px) {
                    justify-content: space-between;
                }

                div {
                    display: flex;
                    flex-direction: column;
                    align-items: flex-start;
                    height: 100%;
                    width: 50%;

                    @media screen and (max-width: 1100px) {
                        width: auto;
                    }

                    h3 {
                        margin-bottom: 1rem;
                        font-size: 24px;
                    }

                    a {
                        color: #fff;
                        text-decoration: none;
                        font-size: 16px;
                        line-height: 2rem;

                        &:hover {
                            text-decoration: underline;
                        }
                    }
                }
            }

            span {
                font-size: 12px;
                font-weight: 400;
                text-align: center;
                margin-top: 2rem;
            }
        }

        &__go-top {
            width: 60px;
            align-items: center;
            justify-content: flex-start;

            a {
                background-color: #fff;
                width: 100%;
                aspect-ratio: 1/1;
                display: flex;
                align-items: center;
                justify-content: center;
                border-radius: 50%;
                text-decoration: none;

                &:hover {
                    background-color: #7D575D;

                    i {
                        color: #fff;
                    }
                }
                
                i {
                    color: #C5AA86;
                font-size: 28px;
                }
            }
        }
    }
</style>