<template>
  <p> {{message}} </p >
</template>

<script>

export default {
    props: {
        message: {
            type: String,
            required: true
        }
    }
}
</script>

<style lang="scss" scoped>
    p{
        color: red;
        text-align: center;
    }
</style>