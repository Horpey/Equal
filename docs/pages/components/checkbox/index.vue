<template>
  <div>
    <h1>Checkbox</h1>

    <Demobox>
      <it-checkbox v-model="checkboxValue" :line-through="lineCheck" :disabled="checkboxDisabled" :type="checkboxType" :pulse="checkboxPulse" :icon="checkboxIcon" :label="checkboxLabel"  />
      <template slot="props">
        <it-select placeholder="Select type" labelTop="Checkbox type" v-model="checkboxType">
          <it-select-option :key="type" v-for="type in checkboxTypes" :value="type">{{type}}</it-select-option>
        </it-select>
        <it-input v-model="checkboxLabel" labelTop="Checkbox label" />
        <it-checkbox label="Line through" v-model="lineCheck" />
        <it-input v-model="checkboxIcon" labelTop="Checkbox icon" />
        <it-checkbox label="Pulse" v-model="checkboxPulse" />
        <it-checkbox label="Disabled" v-model="checkboxDisabled" />
      </template>
    </Demobox>

    <Box :code="codeType" title="Type">
      <it-checkbox type="primary" label="Primary" v-model="typesCheck" />
      <it-checkbox type="success" label="Success" v-model="typesCheck" />
      <it-checkbox type="danger" label="Danger" v-model="typesCheck" />
      <it-checkbox type="warning" label="Warning" v-model="typesCheck" />
      <it-checkbox type="black" label="Black" v-model="typesCheck" />
      <it-checkbox type="neutral" label="Neutral" v-model="typesCheck" />
    </Box>

    <Box :code="codeLine" title="LineThrough">
      <it-checkbox type="primary" label="Click me" v-model="lineCheck" line-through />
    </Box>

    <Box :code="codeIcon" title="Icon">
      <it-checkbox type="primary" label="Primary" icon="visibility" v-model="iconsCheck" />
      <it-checkbox type="success" label="Success" icon="room" v-model="iconsCheck" />
      <it-checkbox type="danger" label="Danger" icon="favorite" v-model="iconsCheck" />
      <it-checkbox type="warning" label="Warning" icon="alarm_on" v-model="iconsCheck" />
      <it-checkbox type="black" label="Black" icon="verified_user" v-model="iconsCheck" />
      <it-checkbox type="neutral" label="Neutral" icon="refresh" v-model="iconsCheck" />
    </Box>

    <Box :code="codePulse" title="Pulse">
      <p slot="description" style="padding: 0px 24px;">Pulse helps you to catch user's attention</p>
      <it-checkbox type="primary" pulse label="Look at me" v-model="pulseValue" />
    </Box>

    <props-table :data-sheet="dataSheet" />
  </div>
</template>

<script lang="ts">
import Demobox from '~/components/Demobox.vue'
import Box from '~/components/Box.vue'
import PropsTable from '~/components/Table.vue'
import { Component, Prop, Vue } from 'vue-property-decorator'

@Component({
  // @ts-ignore
  layout: 'components',
  components: { Demobox, Box, PropsTable }
})
export default class CheckboxPage extends Vue {
  public checkboxDisabled = false
  public checkboxValue = false
  public checkboxPulse = false
  public checkboxLabel = 'Checkbox'
  public checkboxIcon = 'check'
  public checkboxType = 'primary'
  public checkboxTypes = ['primary', 'success', 'danger', 'warning', 'black', 'neutral']

  public typesCheck = true
  public iconsCheck = true
  public lineCheck = false
  public pulseValue = false

  public codeType = `<it-checkbox type="primary" label="Primary" v-model="typesCheck" />
<it-checkbox type="success" label="Success" v-model="typesCheck" />
<it-checkbox type="danger" label="Danger" v-model="typesCheck" />
<it-checkbox type="warning" label="Warning" v-model="typesCheck" />
<it-checkbox type="black" label="Black" v-model="typesCheck" />
<it-checkbox type="neutral" label="Neutral" v-model="typesCheck" />`

  public codeIcon = `<it-checkbox type="primary" label="Primary" icon="visibility" v-model="iconsCheck" />
<it-checkbox type="success" label="Success" icon="room" v-model="iconsCheck" />
<it-checkbox type="danger" label="Danger" icon="favorite" v-model="iconsCheck" />
<it-checkbox type="warning" label="Warning" icon="alarm_on" v-model="iconsCheck" />
<it-checkbox type="black" label="Black" icon="verified_user" v-model="iconsCheck" />
<it-checkbox type="neutral" label="Neutral" icon="refresh" v-model="iconsCheck" />`

  public codePulse = `<it-checkbox type="primary" pulse label="Look at me" v-model="pulseValue" />`

  public codeLine = `<it-checkbox type="primary" label="Click me" v-model="lineCheck" line-through />`

  public dataSheet = [
    {
      property: 'type',
      type: ['String'],
      default: 'primary',
      values: ['primary', 'success', 'danger', 'warning', 'black', 'neutral'],
      description: 'Type of the checkbox'
    },
    {
      property: 'label',
      type: ['String'],
      default: '',
      values: [],
      description: 'Label of the checkbox'
    },
    {
      property: 'icon',
      type: ['String'],
      default: 'check',
      values: ['Material Icons'],
      description: 'Icon of the checkbox'
    },
    {
      property: 'line-through',
      type: ['Boolean'],
      default: false,
      values: [],
      description: 'Adds line-through on label when checked'
    },
    {
      property: 'disabled',
      type: ['Boolean'],
      default: false,
      values: [],
      description: 'Makes checkbox disabled'
    },
    {
      property: 'value (v-model)',
      type: ['Boolean'],
      default: false,
      values: [],
      description: 'Checkbox value'
    },
    {
      property: 'pulse',
      type: ['Boolean'],
      default: false,
      values: [],
      description: 'Add pulse to the element'
    }
  ]
}
</script>
