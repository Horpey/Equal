<template>
  <div class="it-demobox">
    <div class="it-demobox-scene">
      <slot></slot>
    </div>
    <div class="it-demobox-props">
      <h3 style="margin-top: 0px;">Props</h3>
      <slot name="props"></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: 'demobox'
}
</script>

<style lang="less">
  .it-demobox {
    background: #ffffff;
    border: 1px solid #D3DAE6;
    border-radius: 4px;
    display: flex;
    width: 100%;
    min-height: 200px;

    &-scene {
      justify-content: center;
      align-items: center;
      flex-wrap: wrap;
      flex: 5;
      display: flex;
      overflow: scroll;
      overflow: hidden;
    }

    &-props {
      display: flex;
      flex-direction: column;
      padding: 10px 15px;
      flex: 2;
      border-left: 1px solid #D3DAE6;
    }

    &-props > * {
      margin-bottom: 12px;
    }
  }

  .it-demobox + .table-box {
    margin-top: 30px;
  }
  @media only screen and (max-width: 600px) {
    .it-demobox {
      flex-direction: column;
      &-scene {
        padding: 20px 0px;
      }

      &-props {
        border-top: 1px solid #D3DAE6;
        border-left: none;
      }
    }
  }
</style>