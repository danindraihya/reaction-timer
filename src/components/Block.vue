<template>
  <div class="block" v-if="showBlock" @click="stopCount" >
      Click Menu
  </div>
</template>

<script>
export default {
    name: 'Block',
    props: ['delay'],
    data() {
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0
        }
    },
    methods: {
        startCount() {
            this.timer = setInterval(() => { this.reactionTime += 10 }, 10)
        },
        stopCount() {
            clearInterval(this.timer)
            this.$emit('end', this.reactionTime)
        }


    },
    mounted() {
        setTimeout(() => {
            this.showBlock = true
            this.startCount()
        }, this.delay)
    }

};
</script>

<style scoped>
.block {
    margin: 40px auto;
    padding: 100px 0;
    width: 400px;
    text-align: center;
    color: white;
    text-align: center;
    background-color: teal;
    border-radius: 20px;
}
</style>