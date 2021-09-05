<template>
  <div class="input-group">
    <span class="input-group-addon">
      <input type="checkbox" aria-label="..." :checked="status === 'clear'" @change="changeStatus" />
    </span>
    <input type="text" class="form-control" v-model="title" aria-label="..." />
    <span class="input-group-btn">
      <button class="btn btn-default" type="button" @click="removeItem">X</button>
    </span>
  </div>
  <!-- /input-group -->
</template>

<script lang="ts">
import { Vue, Component, Prop } from 'vue-property-decorator';

@Component
export default class Item extends Vue {
  @Prop() public readonly id!: string;
  @Prop() public readonly title!: string;
  @Prop() public readonly status!: 'active' | 'clear';

  public changeStatus($event: Event) {
    const checked: boolean = $event.target.checked;
    if (checked) {
      this.$store.commit('changeStatus', { id: this.id, status: 'clear' });
    } else {
      this.$store.commit('changeStatus', { id: this.id, status: 'active' });
    }
  }
  public removeItem() {
    this.$store.commit('removeItem', this.id);
  }
}
</script>

<style>
.input-group {
  margin-bottom: 1rem;
}
</style>