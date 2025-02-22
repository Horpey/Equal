<template>
  <Button
    class="it-btn"
    :class="[
      type ? `it-btn--${type}` : 'it-btn--primary',
      outlined && `it-btn--outlined`,
      size && `it-btn--${size}`,
      round && 'round',
      (pulse && !disabled) && 'pulse',
      block && 'it-btn--block'
    ]"
    :style="[!$slots.default && {padding: '9px 9px'}]"
    :disabled="disabled"
    v-on="$listeners"
  >
    <it-icon
      v-if="icon && !iconAfter"
      :name="icon"
      :style="{visibility: loading ? 'hidden': 'visible', ...($slots.default && marginStyle)}"
    />
    <span
      v-if="$slots.default"
      :style="{visibility: loading ? 'hidden': 'visible'}"
      class="it-btn-text"
    >
      <slot />
    </span>
    <it-icon
      v-if="icon && iconAfter"
      :name="icon"
      :style="{visibility: loading ? 'hidden': 'visible', ...($slots.default && marginStyle)}"
    />
    <it-loading
      color="#fff"
      :radius="10"
      :style="{
        position: 'absolute',
        left: '50%',
        top: '50%',
        marginLeft: '-10px',
        marginTop: '-10px'
      }"
      :stroke="3"
      v-if="loading"
    ></it-loading>
  </Button>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator'
import './button.less'
import { Sizes } from '../../models'
import { Colors } from '../../models'

@Component
export default class ItButton extends Vue {
  @Prop({
    default: Colors.NEUTRAL,
    validator: (value) => [
        Colors.PRIMARY,
        Colors.SUCCESS,
        Colors.DANGER,
        Colors.WARNING,
        Colors.BLACK,
        Colors.NEUTRAL
      ].includes(value)
  })
  private type!: string
  @Prop({
    default: 'normal',
    validator: (value) => [
      Sizes.SMALL,
      Sizes.NORMAL,
      Sizes.BIG
    ].includes(value)
  })
  private size?: string
  @Prop({ type: Boolean, default: false }) private iconAfter!: boolean
  @Prop({ type: Boolean, default: false }) private disabled!: boolean
  @Prop({ type: Boolean, default: false }) private outlined!: boolean
  @Prop({ type: Boolean, default: false }) private round!: boolean
  @Prop({ type: Boolean, default: false }) private pulse!: boolean
  @Prop({ type: Boolean, default: false }) private loading!: boolean
  @Prop({ type: Boolean, default: false }) private block!: boolean
  @Prop() private icon!: string

  private marginStyle = this.iconAfter
    ? { marginLeft: '6px' }
    : { marginRight: '6px' }
}
</script>

