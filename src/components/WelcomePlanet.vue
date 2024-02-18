<template>
    <div>
        <div class="WelcomeImage">
            <img :src="WelcomeData.hdrul">
        </div>
        <div class="title">{{ WelcomeData.title }}</div>
        <div class="text">{{ WelcomeData.explanation }}</div>
    </div>
</template>

<script>
export default {
    name: 'WelcomePlanet',
    created() {
        fetch('https://api.nasa.gov/planetary/apod?api_key=QGyyDNOO1J1tJGOQOjwhxnidqkZfl2ICYbV6ZeTi')
        .then((res)=>{
            res.json().then((data)=>{
                this.WelcomeData = {
                    hdurl: data.hdrul,
                    title: data.title,
                    explanation: data.explanation,
                }
            })
        })
    },
    data() {
        return {
            WelcomeData: {
                hdrul: '',
                title: "",
                explanation: "",
            }
        }
    }
}
</script>

<style scoped>

.WelcomeImage{
    width: 100vw;
    height: 100vh;
    position: relative;
}
.WelcomeImage> img{
    width: 100vw;
    height: 100vh;  
}
.title{
    font-size: 32px;
    color: #fff;
    top: 45%;
    position: absolute;
    left: 25%;
    font-weight: 500;
}
.text{
    font-size: 32px;
    color: #fff;
    top: 50%;
    position: absolute;
    left: 20%;
    letter-spacing: 2px;
    font-weight: 400;
}
</style>