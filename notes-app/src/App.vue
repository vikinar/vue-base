<template>
<div class="wrapper">
  <div class="wrapper-content">
    <section>
      <div class="container">
        <h1>{{title}}</h1>
        
        <Message v-if='message' :message = 'message'/>
        
        <newNote 
          :note = 'note'
          @addNote = 'addNote'
        />

        <notes :notes = 'notes' @remove = 'removeNote'/>

      </div>
    </section>
  </div>
</div>
</template>

<script>

import Message from '@/components/Message'
import newNote from '@/components/NewNote'
import notes from '@/components/Notes'

export default {
  components: {
    Message, newNote, notes
  },
  data() {
    return {
        title: 'Notes app',
        message: null,
        note: {
          title: '',
          descr: ''
        },
        notes: [
          {
            title: 'First Note',
            descr: 'Description for first note',
            date: new Date(Date.now()).toLocaleString()
          },
                  {
            title: 'Second Note',
            descr: 'Description for second note',
            date: new Date(Date.now()).toLocaleString()
          },
                  {
            title: 'Third Note',
            descr: 'Description for third note',
            date: new Date(Date.now()).toLocaleString()
          }
        ]
      }
    },
    methods: {
      addNote(){
        let {title, descr} = this.note

        if(title === ''){
          this.message = `Title can't be blank`
          return false
        }

        this.notes.push({
          title,
          descr,
          date: new Date(Date.now()).toLocaleString()
        })
        this.message = null
        title = ''
        descr = ''
      },
      removeNote(index){
        this.notes.splice(index, 1)
      }
    }
  }
</script>

<style>
</style>
