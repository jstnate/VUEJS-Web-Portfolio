<template>
    <nav class="nav-bar">
        <span>
            <span class="txt-rotate wrap" data-period="1000" data-rotate='[ "@jstnate", "Web Portfolio", "Home Page", "Nathan LEFETEY"]'></span>
        </span>

        <ul class="menu">
            <li><a href="#my-services">Mes Services</a></li>
            <li><a href="#my-projects">Mes Projets</a></li>
            <li><a href="#my-skills">Mes Compétences</a></li>
        </ul>

        <div class="hamburger hamburger--arrowalt js-hamburger">
            <div class="hamburger-box">
                <div class="hamburger-inner"></div>
            </div>
        </div>
    </nav>
</template>
<script>
    export default {
        name: "NavLayout",
        mounted() {
            let hamburger = document.querySelector('.hamburger');
            let menu = document.querySelector('.menu');
            let nav = document.querySelector('.nav-bar');

            hamburger.addEventListener('click', function() {
                hamburger.classList.toggle('is-active');
                menu.classList.toggle('is-active');
            });

            // Ajoutez un écouteur d'événements à l'objet global window
            window.addEventListener('click', function(event) {
            // Vérifiez si l'élément cliqué fait partie de la liste .menu ou pas
            if (!menu.contains(event.target) && !hamburger.contains(event.target)) {
                // L'utilisateur a cliqué en dehors de la liste .menu
                menu.classList.remove('active');
            }
            });

            window.addEventListener('scroll', function() {
                if (window.scrollY > 0) {
                    nav.classList.add('scrolled');
                } else {
                    nav.classList.remove('scrolled');
                }
            });

            //  TEXT HEADER ANIM SCRIPT (Library)
            let TxtRotate = function(el, toRotate, period) {
                this.toRotate = toRotate;
                this.el = el;
                this.loopNum = 0;
                this.period = parseInt(period, 10) || 1000;
                this.txt = '';
                this.tick();
                this.isDeleting = false;
            };

            TxtRotate.prototype.tick = function() {
                var i = this.loopNum % this.toRotate.length;
                var fullTxt = this.toRotate[i];

                if (this.isDeleting) {
                    this.txt = fullTxt.substring(0, this.txt.length - 1);
                } else {
                    this.txt = fullTxt.substring(0, this.txt.length + 1);
                }

                this.el.innerHTML = '<span class="wrap">'+this.txt+'</span>';

                var that = this;
                var delta = 200 - Math.random() * 100;

                if (this.isDeleting) { delta /= 2; }

                if (!this.isDeleting && this.txt === fullTxt) {
                    delta = this.period;
                    this.isDeleting = true;
                } else if (this.isDeleting && this.txt === '') {
                    this.isDeleting = false;
                    this.loopNum++;
                delta = 500;
                }

                setTimeout(function() {
                that.tick();
                }, delta);
            };

            window.onload = function() {
                var elements = document.getElementsByClassName('txt-rotate');
                for (var i=0; i<elements.length; i++) {
                var toRotate = elements[i].getAttribute('data-rotate');
                var period = elements[i].getAttribute('data-period');

                if (toRotate) {
                    new TxtRotate(elements[i], JSON.parse(toRotate), period);
                }
                }

                // INJECT CSS
                var css = document.createElement("style");
                css.type = "text/css";
                css.innerHTML = ".txt-rotate > .wrap { border-right: 0.2em solid #C5AA86 }";
                document.body.appendChild(css);
            };
        }
    }
</script>
<style lang="scss" scoped>
    .nav-bar {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 0 3rem;
        height: 10vh;
        font-size: 20px;
        font-weight: bold;
        font-family: 'Unbounded', cursive !important;
        background-color: transparent;
        transition: all .3s;
        z-index: 99;

        &.scrolled {
            background-color: #F9F9F9;
            box-shadow: 0 8px 16px -8px rgba(0, 0, 0, .2);
        }

        span {
            color: #C5AA86;
            width: 250px;
            font-size: 16px;
            width: 50%;

            .wrap {
                font-size: 16px;
            }
        }

        .menu {
            width: 50%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            color: #7D575D;
            list-style: none;
            transform: translate(0);

            @media screen and (max-width: 1024px) {
                position: absolute;
                display: flex;
                top: 0;
                right: 0;
                flex-direction: column;
                align-items: center;
                justify-content: center;
                gap: 25px;
                background: rgb(125, 87, 93);
                width: 60vw;
                height: 100vh;
                transform: scaleX(0);
                transform-origin: right center;
                transition: transform .3s ease;
            }

            &.is-active {
                transform: scaleX(1);
            }

            a {
                position: relative;
                color: #7D575D;
                font-size: 16px;
                text-decoration: none;

                @media screen and (max-width: 1024px) {
                    color: #F9F9F9;
                    font-size: 20px;
                }

                &:hover::after {
                    transform: scaleX(1);
                    transform-origin: bottom left;
                }

                &::after {
                    content: '';
                    position: absolute;
                    width: 100%;
                    transform: scaleX(0);
                    height: 2px;
                    bottom: -5px;
                    left: 0;
                    background-color: #7D575D;
                    transform-origin: bottom right;
                    transition: transform 0.25s ease-out;

                    @media screen and (max-width: 1024px) {
                        background-color: #F9F9F9;
                    }
                }
            }

        }

        .hamburger {
            font: inherit;
            display: none;
            overflow: visible;
            margin: 0;
            padding: 15px;
            cursor: pointer;
            transition-timing-function: linear;
            transition-duration: .15s;
            transition-property: opacity,filter;
            text-transform: none;
            color: inherit;
            border: 0;
            background-color: transparent;

            @media screen and (max-width: 1024px) {
                display: block;
            }

            &.is-active {
                .hamburger-box {
                    .hamburger-inner {

                        &, &::before, &::after {
                            background-color: #F9F9F9;
                        }

                        &::before {
                            top: 0;
                            transition: top .1s ease,transform .1s cubic-bezier(.895,.03,.685,.22) .1s;
                            transform: translate3d(-8px,-10px,0) rotate(-45deg) scaleX(.7);
                        }

                        &::after {
                            bottom: 0;
                            transition: bottom .1s ease,transform .1s cubic-bezier(.895,.03,.685,.22) .1s;
                            transform: translate3d(-8px,10px,0) rotate(45deg) scaleX(.7);
                        }
                    }
                }
            }

            .hamburger-box {
                position: relative;
                display: inline-block;
                width: 40px;
                height: 24px;

                .hamburger-inner {
                    transform: rotate(180deg);
                    top: 50%;
                    display: block;
                    margin-top: -2px;

                    &, &::before, &::after {
                        position: absolute;
                        width: 40px;
                        height: 4px;
                        transition-timing-function: ease;
                        transition-duration: .15s;
                        transition-property: transform;
                        border-radius: 4px;
                        background-color: #C5AA86;
                        
                    }

                    &::before, &::after {
                        display: block;
                        content: "";
                    }

                    &::before {
                        top: -10px;
                        transition: top .1s ease .1s,transform .1s cubic-bezier(.165,.84,.44,1);
                    }

                    &::after {
                        transition: bottom .1s ease .1s,transform .1s cubic-bezier(.165,.84,.44,1);
                        bottom: -10px;
                    }
                }
            }
        }
    }
</style>
