<template>
    <section class="section-bg color-white p-10">
        <div class="container">
            <div class="text-container">
                <span>The Theme</span>
                <span>You Will Fall For</span>
                <span>A design like never before</span>
                <div class="color-white wait my-5 text-s">I'm a full-time frontend developer with a passion for great design and user experiences. </div>
            </div>
            <div class="text-center"><img width="100%" class="wait" :src="currentSus"></div>
        </div>
        <div class="container">
            <div class="bg-skills wait">
                <div class="col-6" v-for="(s, i) in skills" :key="i">
                    <div class="p-4 d-flex align-items-center" @mouseenter="changeGifBg(s)">
                        <img width="30px" :draggable="false" :src="s.img">
                        <div class="w-100 ml-10">
                            <div class="name mb-10">{{s.name}}</div>
                            <div class="wrapper">
                                <div class="progress-bar">
                                    <span class="progress-bar-fill" :style="{width: `${s.percentage}%`, backgroundColor: `${s.color}`}"></span>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <div class="container-noflex wait">
            <div class="mt-20 text-l">About Myself <span>&#x2198;</span> </div>
            <div class="mt-20 d-flex align-items-center">
                <div class="font-18 text-grey">
                    <p class="mt-10">My name is Adrian Anilraj, I am currently {{yearsOld}} years old. I live in Kuala Lumpur, Malaysia
                    and I am a self-taught developer.</p>
                    <p class="mt-10">Working as a frontend developer has always been my passion ever since 
                        I've graduated from HELP University.</p>
                    <p class="mt-10">
                        I see myself as an energetic, ambitious person who has 
                        developed a matured and responsible approach to any given task or situation I am presented with.</p>
                    <p class="mt-10">
                        My goal is to work towards on becoming a Full-Stacked Developer that will allow me to channel my creativity through 
                        website designing and experience.</p>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
export default {
    name: 'Homepage',
    data() {
        return {
            title: 'The theme you will fall for. A design like never before',
            yearsOld: new Date().getFullYear() - 1998,
            currentSus: require('~/assets/gif/npm.gif'),
            skills: [
                {
                    id: 1,
                    name: 'Javascript',
                    img: require('@/assets/img/javascript.png'),
                    percentage: 80,
                    color: '#efdc4f',
                    sus: require('~/assets/gif/javascript.gif')
                },
                {
                    id: 2,
                    name: 'HTML & CSS',
                    img: require('@/assets/img/html.png'),
                    percentage: 100,
                    color: '#f1652a',
                    sus: require('~/assets/gif/html.gif')
                },
                {
                    id: 3,
                    name: 'React.js',
                    img: require('@/assets/img/react.png'),
                    percentage: 70,
                    color: '#60dbfb',
                    sus: require('~/assets/gif/react.gif')
                },
                {
                    id: 4,
                    name: 'Vue.js',
                    img: require('@/assets/img/vue.png'),
                    percentage: 90,
                    color: '#40b984',
                    sus: require('~/assets/gif/vue.gif')
                },
                {
                    id: 5,
                    name: 'C++',
                    img: require('@/assets/img/cplus.png'),
                    percentage: 30,
                    color: '#659bd3',
                    sus: require('~/assets/gif/cplus.gif')
                },
                {
                    id: 6,
                    name: 'NPM',
                    img: require('@/assets/img/npm.png'),
                    percentage: 60,
                    color: '#cc3736',
                    sus: require('~/assets/gif/npm.gif')
                },
            ]
        }
    },
    methods: {
        changeGifBg(data) {
            this.currentSus = data.sus;
        },
    },
}
</script>

<style lang="scss" scoped>

.section-bg {
    background: #171717;
    width: 100%;
}

.container {
    display: flex;
    align-items: center;
    justify-content: space-between;
    max-width: 900px;
    margin: 0 auto;
}
.text-container {
    max-width: 500px;
    width: 100%;
    font-size: 46px;
    transform: scale(0.94);
    animation: scale 3s forwards cubic-bezier(0.5, 1, 0.89, 1);
}

.wait {
    opacity: 0;
    animation: fade-in 2s 2s forwards cubic-bezier(0.11, 0, 0.5, 0);
}

span {
  display: inline-block;
  opacity: 0;
  filter: blur(4px);
}

.bg-skills {
    width: 100%;
    display: flex;
    align-items: center;
    flex-wrap: wrap;
}

.wrapper {
    width: 100%;
}

.progress-bar {
    // width: 100%;
    background-color: #e0e0e0;
    border-radius: 20px;
    box-shadow: inset 0 1px 3px rgba(0, 0, 0, .2);
}

.progress-bar-fill {
    display: block;
    height: 16px;
    // background-color: #659cef;
    border-radius: 20px;
    transition: width 500ms ease-in-out;
}

.container-noflex {
    max-width: 900px;
    width: 100%;
    margin: 0 auto;
}

span:nth-child(1) {
    animation: fade-in 0.8s 0.1s forwards cubic-bezier(0.11, 0, 0.5, 0);
}
span:nth-child(2) {
    animation: fade-in 1.2s 0.1s forwards cubic-bezier(0.11, 0, 0.5, 0);
}
span:nth-child(3) {
    animation: fade-in 1.2s 1s forwards cubic-bezier(0.11, 0, 0.5, 0);
}

@keyframes scale {
  100% {
    transform: scale(1);
  }
}

@keyframes fade-in {
  100% {
    opacity: 1;
    filter: blur(0);
  }
}
</style>