<template>
    <div class="msg-container">
        <p>{{ msg }}</p>
    </div>
</template>

<script>
    export default {
        name:"Msg",
        props: {
            msg:String
        }
    }
</script>


<style scoped>
    .msg-container {
        display: flex;
        background-color: rgb(107, 107, 212);
        height: 80px;
        width: 160px;
        justify-content: center;
        align-items: center;
        text-align: center;
        border: 2px solid rgb(91, 91, 131);
    }

    .msg-container p {
        color: blue;
    }
</style>