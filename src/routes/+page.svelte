<script>
  
  import Component from '../components/Component.svelte';
</script>

<div class="placeholder">
    <p>[Other Web Component]</p>
</div>

<Component/>

<div class="placeholder"><p>[Other Web Component]</p></div>

<style>
    .placeholder{
        width: 100vw;
        height: 90vh;
        background-color: gainsboro;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .placeholder > p {
        color: gray;
        font-family: 'Courier New', Courier, monospace;
        font-weight: 600;
    }
</style>