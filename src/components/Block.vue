<template>
  <div class="block" v-if="showBlock" @click="stopTimer">click me</div>
</template>

<script>
export default {
    props:['delay'],
    data(){
        return{
            showBlock: false,
            timer : null,
            reactionTimer : 0,

        }
    },
    mounted(){
        console.log("component mounted...");
        setTimeout(() => {
            this.showBlock =true;
            this.startTimer();
            // console.log(this.delay);
        }, this.delay)
    },
    // updated(){
    //     console.log("compoent updated...");
    // },
    // unmounted(){
    //     console.log("compoent unmounted...");
    // },
    methods:{
        startTimer(){
            this.timer = setInterval(() => {
                this.reactionTimer+=10;
            }, 10)
        },
        stopTimer(){
            clearInterval(this.timer);
            this.$emit('end', this.reactionTimer)
            // console.log(this.reactionTimer);
        }
    }
};
</script>

<style>
.block {
  width: 400px;
  border-radius: 20px;
  background: #0faf87;
  color: white;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
}
</style>