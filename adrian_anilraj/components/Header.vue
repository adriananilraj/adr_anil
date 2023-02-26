<template>
    <div class="navbar-section pt-15">
        <div class="container">
            <div class="logo">Adrian Anilraj</div>
            <ul class="navbar">
                <li @click="test" class="navbar-items cursor-pointer" v-for="(n, i) in navItems" :key="i">{{n}}</li>
            </ul>            
        </div>

        <!-- <audio src="@assets/audio/ui_hover.mp3" id="alarm"></audio> -->
    </div>
</template>

<script>
export default {
    name: 'Header',
    data() {
        return {
            navItems: ['Introduction', 'Project', 'Contact', 'Dark/Light Mode'],
            audio: ""
        }
    },
    methods: {
        test() {
        }
    }
}
</script>

<style lang="scss" scoped>
.navbar-section {
    color: #757575;
    height: 13rem;
    background: #171717;

    .container {
        display: flex;
        justify-content: space-between;
        align-items: center;
        max-width: 900px;
        width: 100%;
        margin: 0 auto;
        opacity: 0;
        animation: header 2s 1s forwards;
        animation-delay: 2s;

        .navbar {
        display: flex;
    }

    .navbar-items {
        text-decoration: none;
        list-style-type: none;
        padding: 5px 10px;
        transition: color .3s ease-out 100ms;
        &:hover {
            color: #fff;
        }
    }
    }


}

@keyframes header {
    100% {
        opacity: 1;
    }
}

</style>