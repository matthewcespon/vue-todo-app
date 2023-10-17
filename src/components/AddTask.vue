<template>
<div class="grid w-full gap-1.5">
    <form @submit="onSubmit" class="add-form">
        <div class="form-control grid w-full gap-1.5">
            <Label for="taskx">Title</Label>
            <Input id="taskx" placeholder="Give me a title!" type="text" name="text" v-model="text"/>
        </div>
        <div class="form-controlmgrid w-full gap-1.5 margin-100%">
        <Label for="taskx">Task</Label>
        <Textarea  id="taskx" placeholder="Enter Task" type="text" name="taskx" v-model="taskx" />
        </div>

        <div class="form-control
        form-control-check grid w-full gap-2">
        <Button  type="submit">Add!</Button>
        </div>      
    </form>
</div>
</template>

<script setup>
import { Button } from './ui/button'
import { Textarea } from './ui/textarea'
import { Label } from './ui/label'
import { Input } from './ui/input'
import { useForm } from 'vee-validate'
import * as z from 'zod'
import {
  FormControl,
  FormDescription,
  FormField,
  FormItem,
  FormLabel,
  FormMessage,
} from './ui/form'
</script>
<script>
export default {
    name: 'AddTask',
    data() {
        return {
            text:'',
            taskx:'',
            completed:false,
        }
    },
    methods: {
        onSubmit(e) {
            e.preventDefault()
            if(!this.text) {
                alert("Please add a task")
                return
            }
            const newTask = {
                id: Math.floor(Math.random() * 10000),
                text: this.text,
                taskx: this.taskx,
                completed: this.completed
            }
            this.$emit('addTask', newTask)
            this.text=''
            this.taskx=''
            this.completed=false
    
        }
        
    }
}
</script>
<style scoped>
div{
    margin-top: 2%;
}
</style>
