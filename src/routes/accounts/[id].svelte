<script context="module">
  export async function load(ctx) {
    let id = ctx.params.id
    return { props: { id }}
  }
</script>
  
<script>
  import Navigation from '../../components/accounts/Navigation.svelte'

  export let id
</script>

<Navigation />