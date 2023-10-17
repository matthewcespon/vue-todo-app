<template>
  <div :class="[task.completed ? 'completed' :
  '', 'task']">
    <Checkbox :checked = "task.completed" @click="$emit('toggle-completed',task.id)" />
    <Accordion type="single" class="w-full" collapsible>
      <AccordionItem>
        <AccordionTrigger >
          {{ task.text }}
        </AccordionTrigger>
        <AccordionContent>
          <h3>
            {{task.taskx}}
            <i @click="$emit('delete-task',task.id)" class="fas fa-times"></i>
          </h3>
        </AccordionContent>
      </AccordionItem>
    </Accordion>
  </div>
</template>
<script>
export default{
    name:'Task',
    props:{
        task: Object
    },
}
</script>
<script setup>
import { Accordion, AccordionContent, AccordionItem, AccordionTrigger } from './ui/accordion'
import { Checkbox } from './ui/checkbox'
</script>
<style scoped>
.fas {
  color: red;
  text-decoration: none;
  cursor: pointer;  
}
.task {

  margin: 10px;
  padding: 10px 20px;

  /* pointer-events: none; */
}

.task.completed {
  opacity: 50%;
}

.task h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
  /* pointer-events: all; */
}


</style>