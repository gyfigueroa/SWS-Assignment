<script>
  
  import Component from '../components/Component.svelte';
</script>

<div class="placeholder">
    <p>[Other Web Component] <br> <br> | <br> | <br> V </p>
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
        font-weight: 500;
        text-align: center;
    }
</style>