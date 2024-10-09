<script lang="ts">
    export let title = 'Title'
    export let description = ''
</script>

<li class="card bg-base-100 w-96 shadow-xl">
  <div class="card-body">
    <h2 class="card-title">{ title }</h2>
    <p>{ description }</p>
    <div class="card-actions justify-end">
      <button class="btn btn-primary">Edit</button>
    </div>
  </div>
</li>