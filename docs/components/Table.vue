<template>
  <div class="table-box">
    <h2 v-if="dataSheet" class="it-box-title">Props <it-tag v-if="tagName">{{tagName}}</it-tag> </h2>
    <table v-if="dataSheet" class="table">
      <thead>
        <tr>
          <th>Property</th>
          <th>Type</th>
          <th>Default</th>
          <th>Accepted values</th>
          <th>Description</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in dataSheet" :key="item.property">
          <td v-for="(col, name) in item">
            <div
              style="line-height: 2;"
              v-if="!['description', 'property'].includes(name) && Array.isArray(col)"
            >
              <it-tag v-for="i in col" :key="i">{{i}}</it-tag>
            </div>
            <span v-else>{{col}}</span>
          </td>
        </tr>
      </tbody>
    </table>

    <h2 v-if="slotSheet" class="it-box-title">Slots</h2>
    <table v-if="slotSheet" class="table">
      <thead>
        <tr>
          <th>Name</th>
          <th>Description</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in slotSheet" :key="item.property">
          <td v-for="(col, name) in item">
            <span>{{col}}</span>
          </td>
        </tr>
      </tbody>
    </table>

    <h2 v-if="methodSheet" class="it-box-title">Methods</h2>
    <table v-if="methodSheet" class="table">
      <thead>
        <tr>
          <th>Method</th>
          <th>Description</th>
          <th>Arguments</th>
        </tr>
      </thead>
      <tbody >
        <tr v-for="item in methodSheet" :key="item.property">
          <td v-for="(col, name) in item">
            <span>{{col}}</span>
          </td>
        </tr>
      </tbody>
    </table>

    <h2 v-if="eventSheet" class="it-box-title">Events</h2>
    <table v-if="eventSheet" class="table">
      <thead>
        <tr>
          <th>Event</th>
          <th>Description</th>
          <th>Arguments</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in eventSheet" :key="item.property">
          <td v-for="(col, name) in item">
            <span>{{col}}</span>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator'

@Component
export default class PropsTable extends Vue {
  @Prop() public tagName?: string
  @Prop() public dataSheet!: object[]
  @Prop() public eventSheet!: object[]
  @Prop() public methodSheet!: object[]
  @Prop() public slotSheet!: object[]
}
</script>

<style lang="less">
.table-box {
  border: 1px solid #d3dae6;
  border-radius: 4px;
  display: flex;
  flex-direction: column;
  overflow: hidden;
  box-sizing: border-box;
  overflow-x: auto;

  & + & {
    margin-top: 40px;
  }
}

.table {
  width: 100%;
  border-collapse: collapse;
  background-color: #ffffff;

  & thead {
    background-color: #fafbfd;
    border-bottom: 1px solid #d3dae6;
    border-top: 1px solid #d3dae6;
  }

  & th,
  td {
    line-height: 1;
    text-align: left;
    padding: 10px 16px;
    font-size: 13px;
    font-weight: 500;
  }

  & td {
    font-size: 13px;
    font-weight: normal;
    & > .it-tag {
      font-size: 12px !important;
      font-weight: normal;
    }

    & .it-tag + .it-tag {
      margin-left: 4px;
    }
  }

  & tr {
    border-top: 1px solid #D3DAE6;
    border-bottom: 1px solid #D3DAE6;
  }

  tr:last-child {
    border-bottom: none;
  }
}
</style>