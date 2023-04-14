<template>
    <div id="service-card" @mouseenter="onMouseEnter" @mouseleave="onMouseLeave">
        <img :src="require(`@/assets/icons/services-icons/${currentFavicon}`)" alt="icon de service">
        <h3>{{ title }}</h3>
        <p>{{ description }}</p>
    </div>
</template>
<script>
export default {
    name: "ServiceCard",
    props: {
        favicon: {
            type: String,
            required: true
        },
        hoverFavicon: {
          type: String,
          required: true
        },
        title: {
            type: String,
            required: true
        },
        description: {
          type: String,
          required: true
        }
    },
    data() {
        return {
            currentFavicon:  this.favicon
        }
    },
    methods: {
        onMouseEnter() {
            this.currentFavicon = this.hoverFavicon;
        },
        onMouseLeave() {
            this.currentFavicon = this.favicon;
        },
    }
}
</script>
<style lang="scss" scoped>
    div {
        width: 100%;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: flex-start;
        padding: 3rem 1.5rem;
        font-family: 'Josefin sans', sans-serif;
        gap: 15px;
        background: none;
        color: #7D575D;

        &:hover {
            background: #7D575D;
            color: #F9F9F9;
        }

        img, h3, p {
            background: none;
        }

        img {
            width: 50px;
            aspect-ratio: 1/1;
        }

        h3 {
            text-transform: uppercase;
            font-size: 20px;
            font-weight: 600;

            @media screen and (max-width: 580px) {
                font-size: 16px;
            }
        }

        p {
            text-align: center;
        }
    }
</style>
