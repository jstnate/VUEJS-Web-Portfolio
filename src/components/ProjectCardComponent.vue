<template>
    <div>
        <img :src="require(`@/assets/images/projects/${cover}`)" alt="">
        <div class="details">
            <h3>{{ title }}</h3>
            <span>{{ type }}</span>
            <a :href="url">Découvrir</a>
        </div>
    </div>
</template>
<script>
export default {
    name: 'ProjectCardComponent',
    props: {
        cover: {
            type: String,
            required: true
        },
        title: {
            type: String,
            required: true
        },
        type: {
            type: String,
            required: true
        },
        url: {
            type: String,
            required: true
        }
    }
}
</script>
<style lang="scss" scoped>
    .slider__item {
        position: relative;

        &:hover {
            .details {
                display: flex;
            }
        }

        img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .details {
            display: none;
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(125, 87, 93, .8);
            flex-direction: column;
            align-items: center;
            justify-content: center;
            gap: 20px;
            font-family: 'Josefin sans', sans-serif;

            h3 {
                color: #fff;
                font-size: 28px;
                font-weight: 900;
                text-transform: uppercase;
            }

            span {
                color: #fff;
                font-size: 20px;
                font-weight: 300;
            }

            a {
                color: #fff;
                font-size: 20px;
                font-weight: 900;
                margin-top: 30px;
                text-decoration: none;

                &:hover {
                    text-decoration: underline;
                    text-decoration-thickness: 2px;
                    text-underline-offset: 5px;
                }
            }
        }
    }
</style>