<template>
    <b-list-group>
        <b-list-group-item v-for="todo in todos"  
            :key="todo.id"
            class="d-flex justify-content-between align-items-center">
                {{ todo.title }}
            <b-badge variant="primary" 
                @click="submit(todo.id)" 
                @mouseover="$event.target.classList.add('active')"
                @mouseleave="$event.target.classList.remove('active')"
                :class="{ active: hover }"
                pill>hapus</b-badge>
        </b-list-group-item>
    </b-list-group>
</template>

<script>
export default {
    props: [
        'todos',
    ],
    data() {
        return {
            hover: false
        }
    },
    methods: {
        submit(value) {
            this.$emit('delete-todo', value)
        }
    }
}
</script>
