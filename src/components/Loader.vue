<template>
  <div class="lds-dual-ring"></div>
</template>

<script>
export default {
  name: 'Loader'
}
</script>

<style scoped>
  .lds-dual-ring {
    display: inline-block;
    width: 80px;
    height: 80px;
    margin: 15% auto;
  }
  .lds-dual-ring:after {
    content: " ";
    display: block;
    width: 64px;
    height: 64px;
    margin: 8px;
    border-radius: 50%;
    border-width: 6px;
    border-style: solid;
    border-color: #4FCD8C transparent #4FCD8C transparent;
    animation: lds-dual-ring 1.2s linear infinite;
  }
  @keyframes lds-dual-ring {
    0% {
      transform: rotate(0deg);
    }
    100% {
      transform: rotate(360deg);
    }
  }
</style>
