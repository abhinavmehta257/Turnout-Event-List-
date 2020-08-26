<template id="">
  <div class="form" >
    <h4>Add an Evnet <input type="checkbox" v-model='showform'></h4>
    <div class="event-form" v-if='showform' >
      <div class="form-group">
        <label>Title</label>
        <input type="text" class="form-control" v-model='event.title'>
      </div>
      <div class="form-group">
        <label>Discription</label>
        <textarea type="text" class="form-control" v-model='event.description'></textarea>
      </div>
      <div class="form-group">
        <label>Date</label>
        <input type="date" class="form-control" v-model='event.date'>
      </div>
      <div class="form-group">
        <label>Locaton</label>
        <input type="text" class="form-control" v-model='event.location'>
      </div>
        <button class="btn btn-outline-primary" @click='addEvent'type="button" name="button">Add Event</button>
    </div>
  </div>

</template>

<script type="text/javascript">
import {eventRef} from '../firebaseApp'

  export default{
    data(){
      return {
        event: {
          title:'',
          description:'',
          date:'',
          location:'',
          email:''
        },
        showform:''
      }
    },
    methods:{
      addEvent(){
        this.event.email = this.$store.state.user.email
        eventRef.push(this.event)
      }
    }
  }
</script>
