<template>
  <div>The score is: {{ reactionTime }}</div>
</template>

<script>
  export default {
    props: ["reactionTime"],
    mounted(){
        console.log('Results component mounted');
    }
  };
</script>

<style scoped></style>
