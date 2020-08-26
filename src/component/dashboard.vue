<template id="">
  <div>
    <h3>Events</h3>
    <button class="btn btn-outline-danger btn-sm signOut-btn" @click='signOut'>SIGN OUT</button>
    <hr>
    <AddEvent />
    <hr>
    <div class="col-md-12">
      <div class="row">
        <Eventitem
          v-for='(event ,index) in $store.state.events'
          :event = event

        />
      </div>
    </div>
  
<!--  {{$store.state.events}}-->
  </div>
</template>

<script type="text/javascript">
import Eventitem from './Eventitem'
  import {firebaseApp, eventRef} from '../firebaseApp.js'
  import AddEvent from './AddEvent.vue'

  export default {
    methods:{
      signOut(){
        this.$store.dispatch('signOut')
        firebaseApp.auth().signOut()
      }
    },
    components:{
      AddEvent,
      Eventitem
    },
    mounted(){
      eventRef.on('value',snap => {
        let events = []
        snap.forEach(event => {
          events.push(event.val())
        });
        this.$store.dispatch('setEvents', events)
      })
    }
  }
</script>
