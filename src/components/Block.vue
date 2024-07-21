<template>
  <div class="block" v-if = "showBlock" @click="stopTimer">Click Here {{ delay }}</div>
</template>

<script>
export default {
    props: ["delay"],
    data(){
        return {
            showBlock : false,
            score : 0,
            timer : null
        }
    },

    mounted(){
        setTimeout(() => {
            this.showBlock = true;
            this.startTimer()
        }, this.delay);
    },

    methods: {
        startTimer(){
            this.timer = setInterval(() => {
                this.score += 50;
            },50)
        },
        stopTimer(){
            clearInterval(this.timer);
            this.$emit("endGame",this.score)
        }
    }
}
</script>

<style>
    .block {
        background-color: aqua;
        width: 400px;
        height: 400px;
        margin: 30px auto;
        display: flex;
        justify-content: center;
        align-items: center;
        font-size: 30px;
        font-weight: 600;
        cursor: pointer;
    }
</style>