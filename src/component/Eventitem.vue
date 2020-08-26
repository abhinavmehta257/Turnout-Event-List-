<template id="">
    <div class="col-md-4">
      <div class="event-card p-3">
        <h4 class="card-title">{{event.title}}</h4>
        <p class="card-text">{{event.description}}</p>
        <ul class="list-group list-group-flush">
          <li class="text-muted">Date: {{event.date}}</li>
          <li class="text-muted">Location: {{event.location}}</li>
          <li class="text-muted">Host: {{event.date}}</li>
        </ul>
      </div>
    </div>
</template>

<script type="text/javascript">
  export default{
    props:['event']
  }
</script>
