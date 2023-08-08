<template>
  <p>Reaction Time: {{score}}ms</p>
  <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
    props: ['score'],
    data(){
        return {
            rank: null
        }
    },
    mounted(){
        if(this.score < 250){
            this.rank = "perfect!!!!"
        }
        else if(this.score < 400 ){
            this.rank= " not bad"
        }
        else{

            this.rank = "OOPS! "
        }
    }


}
</script>

<style>
.rank {
    font-size: 1.4em;
    color: #0faf78;
    font-weight: bold;


}
</style>