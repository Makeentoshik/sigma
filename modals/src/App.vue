<template>
 <div class="wrapper">
   <div class="wrapper-content">
  <section>

<!--first modal -->
<div class="container">
<button class="btn btnPrimary" @click="modalFirst = !modalFirst">Show first modal</button>

<modals
 title="First modal"
 v-if="modalFirst"
 @close="modalFirst = !modalFirst">
 <!-- body -->
 <div slot="body">
   <p>Text Text</p>
   <button class="btn btnPrimary" @click="modalFirst = !modalFirst">Well Done!</button>
 </div>
 </modals>

<!-- second modal -->
<button class="btn btnPrimary" @click="modalSecond.show = !modalFirst">Show  modal with <form action=""></form></button>
<modals
 title="Modal with form"
 v-if="modalSecond.show"
 @close="modalSecond.show = false">
 <!-- body -->
 <div slot="body">
   <form @submit.prevent="submitSecondForm">
     <label>Name:</label>
     <input type="text" v-model="modalSecond.name">
    <label>Email:</label>
    <input type="text" v-model="modalSecond.email">
   <button class="btn btnPrimary" >Submit!</button>
   </form>
 </div>
 </modals>

</div>

  </section>
 

   
    
  
  </div>
  </div>
</template>

<script>
import modals from '@/components/Modal.vue'
export default {
  components: { modals },
  data () {
    return {
      modalFirst: false,
      modalSecond: {
        show: false,
        name: '',
        email: ''
      }
    }
  },
  methods: {
    submitSecondForm () {
      console.log({
        name: this.modalSecond.name,
        email: this.modalSecond.email
      })
      this.modalSecond.name = ''
      this.modalSecond.email = ''
      this.modalSecond.show = false
    }
  }
}
</script>

<style>

</style>
