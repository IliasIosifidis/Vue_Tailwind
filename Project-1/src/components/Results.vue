<template>
  <p class="text-xl">Reaction time - {{ score }} ms</p>
  <p class="text-2xl">Rank: <span class="text-4xl text-rose-600 text-shadow-md text-shadow-pink-200">{{ rank }}</span></p>
</template>

<script>
export default{
  props: ['score'],
  data(){
    return {
      rank:null
    }
  },
  mounted(){
    if (this.score < 250){
      this.rank = 'Quick!'
    } else if (this.score < 400){
      this.rank = "Nes-quick"
    } else if (this.score < 600){
      this.rank = "Granma speed 👵"
    } else {
      this.rank = "...any day now"
    }
  }
}

</script>