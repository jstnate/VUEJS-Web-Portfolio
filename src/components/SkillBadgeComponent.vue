<template>
    <div class="single-skill">
        <i :class="icon"></i>
        <span>{{ title }}</span>
    </div>
</template>
<script>
export default {
    name: 'SkillBadgeComponent',
    props: {
        icon: {
            type: String,
            required: true
        },
        title: {
            type: String,
            required: true
        },
    }
}
</script>
<style lang="scss" scoped>
    .single-skill {
        background: none;
        display: flex;
        align-items: center;
        gap: 15px;
        padding: 10px 30px;

        @media screen and (max-width: 580px) {
            flex-direction: column;
        }

        &:hover {
            background: #F9F9F9;
            border-radius: 10px;

            i, span {
                color: #7D575D;
            }
        }
        
        i {
            color: #F9F9F9;
            font-size: 40px;
            background: none;
            width: 50px;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        span {
            color: #F9F9F9;
            background: none;
            font-size: 24px;
            font-weight: 900;
            font-family: 'Josefin Sans', sans-serif;

        }
    }
</style>