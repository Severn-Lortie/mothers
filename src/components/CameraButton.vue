<template>
<div class="button" @click="$emit('clicked')">
    Click!
    <div></div>
</div>
</template>

<script>
export default {
    
}
</script>

<style scoped>
.button {
    backface-visibility: hidden;
    position: relative;
    cursor: pointer;
    display: inline-block;
    white-space: nowrap;
    background: #a7adf0;
    border-radius: 0px;
    border: 0px solid #888dc4;
    border-width: 0px 0px 4px 0px;
    padding: 10px 20px 10px 20px;
    color: #fff;
    font-size: initial;
    font-family: Helvetica Neue;
    font-weight: 900;
    font-style: normal
}

.button>div {
    color: #999;
    font-size: 10px;
    font-family: Helvetica Neue;
    font-weight: initial;
    font-style: normal;
    text-align: center;
    margin: 0px 0px 0px 0px
}

.button:hover {
    background: #8e94ce;
}

.button>i {
    font-size: 1em;
    border-radius: 0px;
    border: 0px solid transparent;
    border-width: 0px 0px 0px 0px;
    padding: 0px 0px 0px 0px;
    margin: 0px 0px 0px 0px;
    position: static
}

.button>.ld {
    font-size: initial
}
</style>
