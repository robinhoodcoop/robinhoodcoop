<script>
  import Animate from '/components/Animate.svelte'
  import { screen } from '/stores/screen.js'
</script>

<style type="text/scss">
  section.title {
    grid-area: title;
    align-self: end;
    justify-self: end;

    h1 {
      @include title;
    }
  }

  @media screen and (max-width: 980px) {
    section.title {
      align-self: center;
      justify-self: center;
    }
  }
</style>

<section class="title">
  {#if $screen == 'dashboard'}
    <Animate>
      <h1>Your portfolio</h1>
    </Animate>
  {:else}
    <Animate>
      <h1>Stage Robin Hood Coop</h1>
    </Animate>
  {/if}
</section>
