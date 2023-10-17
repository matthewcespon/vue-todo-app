<template>
    <header>
        <h1>
            {{ title }}
        </h1>
        <Button @click="onClick()" size="sm">Add Task</Button>
    </header>
</template>
<script>
import { Button } from './ui/button'

    export default {
        name: 'Header',
        props: ['title'],
        components:{Button},
        methods: {
            onClick(){
                this.$emit('toggle-add-task')
            }
        }
    }

    
</script>
<style scoped>
header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;

}
h1 {
    text-align: center;
    font-size: 50px;
    margin: 0;
    color: #146152;
}

</style>