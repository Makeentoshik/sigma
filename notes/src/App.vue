<template>
  <div class="wrapper">
    <div class="wrapper-content">
      
      <section>
        <div class="container">
            
           <message v-if="message" :message="message"/>
        
        
        <newNote
         :note="note"
         @addNote="addNote"/>
<div class="note-header">
<h1> {{ title }} </h1>
<search :search="search" placeholder="Find your note"/>
<div class="icons">
    <svg :class="{ active: grid }" @click="grid = true" style="cursor: pointer;"  xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" ><rect x="3" y="3" width="7" height="7"></rect><rect x="14" y="3" width="7" height="7"></rect><rect x="14" y="14" width="7" height="7"></rect><rect x="3" y="14" width="7" height="7"></rect></svg>
    <svg :class="{ active: !grid }" @click="grid = false" style="cursor: pointer;" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="8" y1="6" x2="21" y2="6"></line><line x1="8" y1="12" x2="21" y2="12"></line><line x1="8" y1="18" x2="21" y2="18"></line><line x1="3" y1="6" x2="3" y2="6"></line><line x1="3" y1="12" x2="3" y2="12"></line><line x1="3" y1="18" x2="3" y2="18"></line></svg>
</div>
</div>

          <notes :notes="notes" :grid="grid" @remove="removeNote" />

        </div>
      </section>

        

        

        </div>
    </div>
  
</template>

<script>
import message from '@/components/Message.vue'
import newNote from  '@/components/NewNote.vue'
import notes from  '@/components/Notes.vue'
import search from '@/components/Search.vue'


export default {
    components: {
       message, notes , newNote , search
         
        
    },
data () {
  return {
title: 'Notes App',
search: '',
 message: null,
 grid: true,
    note: {
    title: '',
    descr: ''
},
 notes: [
    {
         title: 'The First Note',
         descr: 'The First Note Description',
         date: new Date(Date.now()).toLocaleString()
      },
      {
         title: 'The Second Note',
         descr: 'The Second Note Description',
         date: new Date(Date.now()).toLocaleString()
      },
      {
          title: 'The Third Note',
          descr: 'The Third Note Description',
          date: new Date(Date.now()).toLocaleString()
         }
     ]
  }
 },
 methods: {
                addNote() {
                    let {title, descr} = this.note
                    if (title === '') {
                        this.message = 'title cant be blank!'
                        return false
                    }

                    this.notes.push({
                        title,
                        descr,
                        date: new Date(Date.now()).toLocaleString(),
                    })
                    this.note.title = ''
                    this.note.descr = ''
                    this.message = null
                }
            },
            removeNote (index) {
                this.notes.splice(index, 1)
            }
}
</script>


<style>
</style>
