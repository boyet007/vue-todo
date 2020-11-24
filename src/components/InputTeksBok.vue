<template>
    <b-container fluid>
        <b-row class="my-1">
            <b-col>
                <b-form-input  
                    type="text"
                    placeholder="Masukkan todo anda"
                    @keyup.enter="submit"
                    v-model="title"
                    ></b-form-input>
            </b-col>
        </b-row>
  </b-container>
</template>

<script>
export default {
    data() {
        return {
            title: ''
        }
    },
    methods: {
        submit() {
            this.$emit('update-title', this.title)
            this.title=''
        }
    }
}
</script>
