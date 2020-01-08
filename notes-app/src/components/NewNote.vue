<template>
    <div class="new-note">
      <input v-model='note.title' type="text">
      <textarea v-model='note.descr'></textarea>
      <button class='btn btnPrimary submitBtn' @click="addNote">Add note</button>
    </div>
</template>

<script>
export default {
    props: {
        note: {
            type: Object,
            required: true
        }
    },
    methods: {
        addNote(){
            this.$emit('addNote', this.note)
        }
    },
}
</script>

<style lang="scss">
    .new-note {
        text-align: center;
    }

    .submitBtn {
        margin: 1rem 0;
    }
</style>