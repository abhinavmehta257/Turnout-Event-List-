<template>
  <div class="col-md-4" @click='switchCharacter'>
    <div class="character-card mt-3">
      <div class="card-block">
        <h4 class="card-title">{{character.name}}</h4>
        <p class="card-text">Height: {{character.height}}</p>
        <p class="card-text">Mass: {{character.mass}}</p>
        <p class="card-text">Hair colour: {{character.hair_color}}</p>
        <p class="card-text">Eye Color: {{character.eye_color}}</p>
      </div>
    </div>
  </div>
</template>

<script type="text/javascript">

  export default{
    props:['id'],
    data(){
      return{
        character:{}
      }
    },
    methods:{
      fetchCharecter(id){
        fetch('https://swapi.dev/api/people/'+id, {
          method:'GET'
        }).then(response => response.json())
        .then(json => this.character = json)
      },
      switchCharacter(){
        let random_id = Math.floor(Math.random()*81)+1
        this.fetchCharecter(random_id)
      },
      removeCharacter(){
        return(this.id)
      }
    },
    created(){
      this.fetchCharecter(this.id)
    }

  }
</script>
