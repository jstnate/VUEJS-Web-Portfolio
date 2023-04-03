<template>
    <nav>
        <span>
            <span class="txt-rotate wrap" data-period="1000" data-rotate='[ "@jstnate", "Web Portfolio", "Home Page", "Nathan LEFETEY"]'></span>
        </span>

        <ul>
            <li><a href="#my-services">Mes Services</a></li>
            <li><a href="#my-skills">Mes Compétences</a></li>
            <li><a href="#my-projects">Mes Projets</a></li>
        </ul>
    </nav>
</template>
<script>
    export default {
        name: "NavLayout",
        mounted() {
            //  TEXT HEADER ANIM SCRIPT (Library)
            var TxtRotate = function(el, toRotate, period) {
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
    nav {
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
        background-color: #F9F9F9;
        box-shadow: 0 8px 16px -8px rgba(0, 0, 0, .2);
        z-index: 99;

        span {
            color: #C5AA86;
            width: 250px;
            font-size: 16px;
            width: 50%;

            .wrap {
                font-size: 16px;
            }
        }

        ul {
            width: 50%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            color: #7D575D;
            list-style: none;

            a {
                position: relative;
                color: #7D575D;
                font-size: 16px;
                text-decoration: none;

                &:hover::after {
                    transform: scaleX(1);
                    transform-origin: bottom left;
                }
            }

            a::after {
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
            }
        }

        .contact-button {
            background-color: #C5AA86;
            color: #FFFFFF;
            padding: .8em 2em;
            border-radius: 10px;
            transition: all .3s;
            font-size: 16px;

            &:hover {
                background-color: #7D575D;
            }
        }
    }
</style>
